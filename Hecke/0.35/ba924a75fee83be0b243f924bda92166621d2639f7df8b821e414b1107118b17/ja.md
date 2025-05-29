```
short_vectors_affine(
    S::ZZLat,
    v::QQMatrix,
    alpha::RationalUnion,
    d::RationalUnion
  ) -> Vector{QQMatrix}
```

与えられた双曲的または負定義の $\mathbb{Z}$-格子 $S$ に対して、ベクトルの集合を返します

$$
\{x \in S : x^2=d, x.v=\alpha \}.
$$

ここで、$v$ は正の平方を持つ $S$ の周囲空間内の与えられたベクトルであり、$\alpha$ と $d$ は有理数です。

出力されるベクトルは、$S$ の周囲空間におけるその座標の形で与えられます。

実装は [Shi15](@cite) のアルゴリズム 2.2 に基づいています。
