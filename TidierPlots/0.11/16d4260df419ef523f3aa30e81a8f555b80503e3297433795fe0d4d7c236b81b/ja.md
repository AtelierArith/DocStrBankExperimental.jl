```
label_bytes(;units=:si, kwargs...)
```

数値を人間が読みやすいバイトサイズを表す文字列に変換します。

# 引数

  * `units`: `:si` は SI 単位（10 の累乗）、`:binary` はバイナリ単位（1024 の累乗）、または特定の単位文字列（例: MB, GiB）を指定できます。
  * `kwargs...`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_bytes(units=:si)
labeler([1024, 2048]) # ["1.02 KB", "2.05 KB"]
```
