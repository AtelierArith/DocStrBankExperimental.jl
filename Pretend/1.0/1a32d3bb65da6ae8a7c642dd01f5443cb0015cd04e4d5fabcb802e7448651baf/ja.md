```
was_not_called(f::Function, args...; kwargs...)
```

関数 `f` が提供された `args` と `kwargs` で全く呼び出されなかった場合、`true` を返します。これは、モック可能な関数を使用したテストスクリプトを実行した後に使用できます。
