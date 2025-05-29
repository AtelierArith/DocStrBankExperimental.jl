```
bd_integrated_pow(abundances::Vector{Int64}, dim::Int64, locality::BDLocality[, max_cardinality])
```

豊富さベクトル `abundances` から統合ベニンカサ-ダウカー演算子を計算します。

得られた値はマイクロスケール $l$ の単位で与えられます。適切な時間の単位で結果を得るために、この関数の戻り値は $l^2$ で割る必要があります。
