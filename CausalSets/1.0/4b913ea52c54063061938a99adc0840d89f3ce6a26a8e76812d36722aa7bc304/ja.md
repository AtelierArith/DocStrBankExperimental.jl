```
bd_pointwise(causet, i, field, dim, locality[, max_cardinality]) -> Float64
```

指定されたフィールド上での点ごとのBD演算子$B ϕ(e_i)$を計算します。ここで、`ϕ(e_j) = field[j]`です。

得られた値はマイクロスケール$l$の単位で表されます。したがって、適切な時間の単位で結果を得るためには、この関数の戻り値を$l^2$で割る必要があります。
