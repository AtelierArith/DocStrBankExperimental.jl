```
project(M::MultinomialSymmetric, p, Y)
```

`Y`を[`MultinomialSymmetric`](@ref) `M`の点`p`での接空間に射影し、結果を`X`に返します。

[DouikHassibi:2019](@cite)のSec. VIからの式は次の通りです。

$$
    \operatorname{proj}_p(Y) = Y - (α\mathbf{1}_n^{\mathrm{T}} + \mathbf{1}_n α^{\mathrm{T}}) ⊙ p,
$$

ここで、$⊙$はハダマール積または要素ごとの積を示し、$\mathbb{1}_n$は長さ$n$の1のベクトルです。2つのベクトル$α ∈ ℝ^{n×n}$は次の方程式を解くことによって与えられます。

$$
    (I_n+p)α =  Y\mathbf{1},
$$

ここで、$I_n$は$n×n$の単位行列であり、$\mathbf{1}_n$は長さ$n$の1のベクトルです。
