```
bd_integrated_pow(causet::AbstractCauset, dim::Int64, locality::BDLocality[, max_cardinality])
```

統合ベニンカサ-ダウカー演算子を計算します。

得られた値はマイクロスケール $l$ の単位で示されます。したがって、この関数の戻り値を適切な時間の単位で得るためには、$l^2$ で割る必要があります。
