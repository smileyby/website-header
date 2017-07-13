关于网页的headers
================

## js 获取headers

```js

// 获取当前页面的头部信息
var req = new XMLHttpRequest();
req.open('GET', document.location, false);
req.send(null);
var headers = req.getAllResponseHeaders().toLowerCase();
console.log(headers);

// jquery 获取响应头信息，即response headers
$.ajax({
    url: "./test.php",
    type: "POST",
    data: {"user" : "min", "pass" : "he"},
    success: function(data, textStatus, jqXHR) {
        alert(jqXHR.getResponseHeader("Server"));
        alert(jqXHR.getResponseHeader("Content-Type"));
        alert(jqXHR.getResponseHeader("X-Powered-By"));
        alert(jqXHR.getResponseHeader("Content-Encoding"));
        alert(jqXHR.getAllResponseHeaders());
        alert(jqXHR.getResponseHeader("Set-Cookie"));      //返回null，不能获取Set-Cookie的值
        alert(data + textStatus);
    }
});

```

## js 设置headers（一般发生在想服务端发送请求时,即request headers）

```js

// jquery
$.ajax({
	url: 'http://urlapi/user/login',
	type: 'POST',
	beforeSend: function(xhr){
        xhr.setRequestHeader('Content-Type','application/json');
        xhr.setRequestHeader('Accept','application/json');
      },
	data: {
		username: 'pippo',
		password: 'secret123'
	},
	dataType： 'json',
	success: function(){
		console.log('succ');
	},
	error: function(){
		console.log('err');
	}
})

```