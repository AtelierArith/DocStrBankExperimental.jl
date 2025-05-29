```
short_vectors_affine
    gram::MatrixElem{T},
    v::MatrixElem{T},
    alpha::RationalUnion,
    d::RationalUnion
  ) where T <: Union{ZZRingElem, QQFieldElem} -> Vector{MatrixElem{T}}
```

与えられたグラム行列 `gram` のハイパーボリックまたは負定義 $\mathbb{Z}$-格子 $S$ に対して、次のベクトルの集合を返します。

$$
\{x \in S : x^2=d, x.v=\alpha \}.
$$

ここで、$v$ は正の平方を持つ与えられたベクトルであり、$S$ の有理スパンの標準基底におけるその座標で表され、$\alpha$ と $d$ は有理数です。

出力されるベクトルは、$S$ の有理スパンにおけるその座標の形で与えられます。

実装は [Shi15](@cite) のアルゴリズム 2.2 に基づいています。
