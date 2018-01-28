# AndroidJSBridge
Android与前端交互之JSBridge的详解<br/>

## JS调用Android<br/>
```
       bridgeWebView.registerHandler("submitFromWeb", new BridgeHandler() {
            @Override
            public void handler(String data, CallBackFunction function) {
                Log.e("TAG", "js返回：" + data);
                //显示js传递给Android的消息
                Toast.makeText(MainActivity.this, "js返回:" + data, Toast.LENGTH_LONG).show();
                //Android返回给JS的消息
                function.onCallBack("我是js调用Android返回数据：" + etText.getText().toString());
            }
        });

```
    
## Android调用JS<br/>

```
        btn.setOnClickListener(new View.OnClickListener() {

            @Override
            public void onClick(View view) {
                bridgeWebView.callHandler("functionInJs", "Android调用js的方法", new CallBackFunction() {
                    @Override
                    public void onCallBack(String data) {
                        Log.e("TAG", "onCallBack:" + data);
                        Toast.makeText(MainActivity.this, data, Toast.LENGTH_LONG).show();
                    }
                });
            }
        });
        
```

详情请查看博客：http://blog.csdn.net/yoonerloop/article/details/78033908
