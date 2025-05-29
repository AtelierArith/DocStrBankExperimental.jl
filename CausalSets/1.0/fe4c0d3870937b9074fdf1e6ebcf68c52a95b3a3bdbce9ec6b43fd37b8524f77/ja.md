```
bd_integrated_pow(causet::AbstractCauset, dim::Int64, locality::BDLocality, ::Val{N}[, max_cardinality])
```

ベニンカサ-ダウカー演算子の統合された `N`-次の冪を計算します。

得られた値はマイクロスケール $l$ の単位で与えられます。したがって、この関数の戻り値を適切な時間の単位で得るためには、$l^{2N}$ で割る必要があります。
