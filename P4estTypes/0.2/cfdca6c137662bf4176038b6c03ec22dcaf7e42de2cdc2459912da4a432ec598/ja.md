```
LNodes{X,P}
```

`Pxest{X}`のためのロバットノードの並行番号を格納します。

# フィールド

  * `pointer`: ポインタ（型 `P`）は、`P4estTypes.P4est.p4est_lnodes_t` または `P4estTypes.P4est.p8est_lnodes_t` のいずれかを指すポインタである可能性があります。これらの型に関する詳細は、ヘルプドキュメントを参照してください。
  * `comm`: lnods に参加しているランクを含む MPI コミュニケーター。

# 参照

  * [`lnodes`](@ref): `LNodes` を構築するために使用される関数
