```
without_authentication(f::Function, session)
without_authentication(f::Function, params::Dict{Symbol,Any})
```

現在のセッションに認証されたユーザーがいない場合、`f`を呼び出します。
