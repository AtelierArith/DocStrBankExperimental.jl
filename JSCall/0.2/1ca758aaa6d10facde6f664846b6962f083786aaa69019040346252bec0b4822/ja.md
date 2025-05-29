Javascriptに格納されたオブジェクトを参照します。次の式をJavascript側の実際の呼び出しにマッピングします：

```julia
jso = JSObject(name, scope, typ)
# getfield:
x = jso.property # 新しいJSObjectを返します
# setfield
jso.property = "newval" # newvalとしてJSObjectsまたはJuliaオブジェクトで動作します
# call:
result = jso.func(args...) # argsとしてjuliaオブジェクトや他のJSObjectsで動作します

# コンストラクタはこのようにラップされます：
scene = jso.new.Scene() # JSと同じ：scene = new jso.Scene()
```
