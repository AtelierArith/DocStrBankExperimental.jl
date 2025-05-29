```
rec2coeff(deg::Int,a::Vector{<:Real},b::Vector{<:Real})
rec2coeff(a,b) = rec2coeff(length(a),a,b)
```

与えられた再帰係数 `(a,b)` によって指定された次数 `deg` までの直交多項式の係数を取得します。この関数は次の式から $c_i^{(k)}$ の値を返します。

$$
p_k (t) = t^d + \sum_{i=0}^{k-1} c_i t^i,
$$

ここで、$k$ は `1` から `deg` まで変化します。

呼び出し `rec2coeff(a,b)` は、与えられた `(a,b)` に対してすべての可能な再帰係数を出力します。
