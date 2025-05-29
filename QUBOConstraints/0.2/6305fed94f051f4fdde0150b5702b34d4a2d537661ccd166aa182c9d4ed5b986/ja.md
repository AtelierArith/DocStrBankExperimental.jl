```
is_valid(x, encoding::Symbol = :none)
```

`x`が`encoding`の有効な形式を持っているかどうかを確認します。

例えば、`encoding == :one_hot`の場合、`x`のビットのうち最大1つだけが1に設定されている必要があります。
