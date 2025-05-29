```
product_distribution(dists::NamedTuple{K,Tuple{Vararg{Distribution}}}) where {K}
```

独立した名前付き分布の積分布としての`NamedTuple`の分布を作成します。

この関数は、[`ProductNamedTupleDistribution`](@ref)分布を構築することにフォールバックしますが、特化したメソッドを定義することもできます。
