```
bd_integrated_pow(abundances::Array{Int64, N}, dim::Int64, locality::BDLocality, ::Val{N}[, max_cardinality])
```

豊富さ配列 `abundances` からベニンカサ-ダウカー演算子の統合された `N` 次の冪を計算します。

得られた値はマイクロスケール $l$ の単位で与えられます。したがって、適切な時間の単位で結果を得るためには、この関数の戻り値を $l^{2N}$ で割る必要があります。
