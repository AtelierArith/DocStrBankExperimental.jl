```
project(M::MultinomialDoubleStochastic, p, Y)
```

`Y`を[`MultinomialDoubleStochastic`](@ref) `M`の点`p`での接空間に射影し、結果を`X`に返します。式は次のようになります。

$$
    \operatorname{proj}_p(Y) = Y - (α\mathbf{1}_n^{\mathrm{T}} + \mathbf{1}_nβ^{\mathrm{T}}) ⊙ p,
$$

ここで、$⊙$はアダマール積または要素ごとの積を示し、$\mathbb{1}_n$は長さ$n$の1のベクトルです。2つのベクトル$α,β ∈ ℝ^{n×n}$は、次の式の解（通常は左擬似逆行列を使用）として計算されます。

$$
    \begin{pmatrix} I_n & p\\p^{\mathrm{T}} & I_n \end{pmatrix}
    \begin{pmatrix} α\\ β\end{pmatrix}
    =
    \begin{pmatrix} Y\mathbf{1}\\Y^{\mathrm{T}}\mathbf{1}\end{pmatrix},
$$

ここで、$I_n$は$n×n$の単位行列であり、$\mathbf{1}_n$は長さ$n$の1のベクトルです。
