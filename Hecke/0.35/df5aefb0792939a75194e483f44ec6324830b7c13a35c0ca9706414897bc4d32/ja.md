```
enumerate_quadratic_triples(
    Q::MatrixElem{T},
    b::MatrixElem{T},
    c::RationalUnion;
    algorithm::Symbol=:short_vectors,
    equal::Bool=false
  ) where T <: Union{ZZRingElem, QQFieldElem}
                          -> Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}
```

与えられた正定値二次形式のグラム行列 $Q$ に対して、$v*Q*v^T + 2*v*Q*b^T + c \leq 0$ を満たすペア $(v, d)$ のリストを返します。ここで、$b$ は行ベクトルとして見なされ、$c$ は有理数です。さらに、$d$ は $(v-b)*Q*(v-b)^T = d$ となるようにします。

現時点では、アルゴリズム `:short_vectors` のみが利用可能です。この関数は、二次トリプル `[Q, b, c]` の最近接ベクトル問題に必要なデータを使用します。特に、$d$ は関連する上限 $M$ より小さいです（[`close_vectors`](@ref) を参照）。

`equal` が `true` に設定されている場合、関数は $d=M$ となるペア $(v, d)$ のみを返します。
