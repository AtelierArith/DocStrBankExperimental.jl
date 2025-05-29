```
is_wrapped_exception(e)::Bool
```

与えられた例外インスタンス `e` がラップされた例外である場合に true を返します。つまり、`unwrap_exception(e)` が `e` とは異なる何かを返す場合です。
