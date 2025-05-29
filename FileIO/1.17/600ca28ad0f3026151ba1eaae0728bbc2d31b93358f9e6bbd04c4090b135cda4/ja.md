```
add_saver(fmt, :Package=>uuid)
add_saver(fmt, [:Package=>uuid, specifiers...])
```

フォーマット `fmt` がパッケージ `:Package` と共に保存できることを宣言します。指定子には特定のオペレーティングシステムに使用を制限するための `OSX`、`Unix`、`Windows`、および `Linux` が含まれます。

また、フォーマット宣言とパッケージサポートを組み合わせることができる [`add_format`](@ref) も参照してください。
