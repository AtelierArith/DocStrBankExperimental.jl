```
iterator(b::Bgen; offsets=nothing, from_bgen_start=nothing)
```

`b`のためのバリアントイテレータを取得します。

  * `offsets`が提供されている場合、または`.bgen.bgi`が提供されていて

`from_bgen_start`が`false`の場合、オフセットのリストを反復する`VariantIteratorFromOffsets`を返します。

  * それ以外の場合、bgenファイルの先頭から最後まで順次反復する`VariantIteratorFromStart`を返します。
