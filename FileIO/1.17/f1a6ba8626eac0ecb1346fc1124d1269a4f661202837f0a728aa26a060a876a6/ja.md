```
add_loader(fmt, :Package=>uuid)
add_loader(fmt, [:Package=>uuid, specifiers...])
```

フォーマット `fmt` がパッケージ `:Package` でロードできることを宣言します。指定子には特定のオペレーティングシステムに使用を制限するための `OSX`、`Unix`、`Windows`、および `Linux` が含まれます。

パッケージサポートとフォーマット宣言を組み合わせることができる [`add_format`](@ref) も参照してください。
