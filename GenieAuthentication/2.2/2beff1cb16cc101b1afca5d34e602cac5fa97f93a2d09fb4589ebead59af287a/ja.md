```
logout(session) :: Sessions.Session
logout(params::Dict{Symbol,Any}) :: Sessions.Session
```

セッションからユーザーオブジェクトのIDを削除し、実質的にユーザーをログオフします。
