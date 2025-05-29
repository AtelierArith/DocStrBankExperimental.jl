```
called_exactly_once(f::Function, args...; kwargs...)
```

関数 `f` が提供された `args` と `kwargs` で正確に1回呼び出された場合は `true` を返します。これは、モック可能な関数を使用したテストスクリプトを実行した後に使用できます。
