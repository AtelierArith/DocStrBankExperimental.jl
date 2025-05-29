```
called_at_least_once(f::Function, args...; kwargs...)
```

関数 `f` が提供された `args` と `kwargs` で少なくとも一度呼び出された場合は `true` を返します。これは、モック可能な関数を使用してテストスクリプトを実行した後に使用できます。
