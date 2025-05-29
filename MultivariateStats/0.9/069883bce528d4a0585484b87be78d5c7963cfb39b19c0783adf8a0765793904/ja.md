```
predict(M::CCA, Z::AbstractVecOrMat{<:Real}, c::Symbol)
```

与えられた [`CCA`](@ref) モデルにより、観測値を共通の空間に変換することができます。次のように表されます。

$$
\mathbf{z}_x = \mathbf{P}_x^T (\mathbf{x} - \boldsymbol{\mu}_x) \\
\mathbf{z}_y = \mathbf{P}_y^T (\mathbf{y} - \boldsymbol{\mu}_y)
$$

ここで、$\mathbf{P}_x$ と $\mathbf{P}_y$ は $X$ と $Y$ の射影行列であり、$\boldsymbol{\mu}_x$ と $\boldsymbol{\mu}_y$ は平均ベクトルです。

パラメータ `Z` は、長さ `dx` または `dy` のベクトル、または各列が観測値である行列のいずれかです。コンポーネントパラメータ `c` は `:x` または `:y` です。
