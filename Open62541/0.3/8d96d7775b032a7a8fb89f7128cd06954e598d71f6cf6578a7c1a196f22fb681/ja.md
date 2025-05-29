```
JUA_UsernamePasswordLogin 
```

は `JUA_UsernamePasswordLogin` オブジェクトを作成します - これは `UA_UsernamePasswordLogin` オブジェクトの同等物ですが、メモリはCではなくJuliaによって管理されます。

以下のメソッドが定義されています：

```
JUA_UsernamePasswordLogin(username::AbstractString, password::AbstractString)
```

例：

```
j = JUA_UsernamePasswordLogin("PeterParker", "IamSpiderman")

```
