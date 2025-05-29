```
with_authentication(f::Function, fallback::Function, session)
with_authentication(f::Function, fallback::Function, params::Dict{Symbol,Any})
```

セッションでユーザーが現在認証されている場合にのみ `f` を呼び出し、そうでない場合は `fallback` が呼び出されます。
