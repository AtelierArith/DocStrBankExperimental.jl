```
bd_pointwise_pow(causet, i, field, dim, locality, ::Val{N}[, max_cardinality]) -> Float64
```

`N`-次の冪点wise BD 演算子、$B^N ϕ(e_i)$ を指定されたフィールド `ϕ(e_j) = field[j]` に対して計算します。

得られた値はマイクロスケール $l$ の単位で示されます。適切な時間の単位で結果を得るために、この関数の戻り値は $l^{2N}$ で割る必要があります。
