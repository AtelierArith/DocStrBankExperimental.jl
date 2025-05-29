```
update!(las::LAS, [attributes]; kws...)
```

`LAS`を更新し、提供された`NamedTuple`としての`attributes`でポイント属性を置き換えます。これは、`LAS`のポイントレコードがメモリにロードされている場合にのみサポートされています。

キーワード引数は、[`LAS`](@ref)の対応するグローバル属性を更新します。これらのうち、`coord_min`、`coord_max`、および`return_counts`のみがインプレースで変更可能です。

参照: [`update`](@ref)
