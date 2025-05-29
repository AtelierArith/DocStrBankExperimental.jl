```
IsEqual(value::StorageScalar) <: QueryOperation
```

等号は二つの目的で使用されます：

  * 比較演算子として、[`IsLess`](@ref)に似ていますが、比較には`<`の代わりに`=`を使用します。
  * ベクトルから単一のエントリを選択するため。これにより、クエリはベクトルから単一のスカラーを選択できます（例：`/ gene = FOX1 : is_marker`）または行列から（例：`/ cell = ATCG / gene = FOX1 : UMIs`）；または行列から単一のベクトルをスライスすることができます（例：`/ cell = ATCG / gene : UMIs`または`/ cell / gene = FOX1 : UMIs`）。
