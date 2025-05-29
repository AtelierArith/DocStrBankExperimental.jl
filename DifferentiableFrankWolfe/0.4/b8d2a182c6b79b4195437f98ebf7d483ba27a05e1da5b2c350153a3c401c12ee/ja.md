```
DiffFW
```

呼び出し可能なパラメータ化ラッパーで、Frank-Wolfeアルゴリズムを使用して `θ -> argmin_{x ∈ C} f(x, θ)` を解決します。これは `θ` に対して暗黙的に微分可能です。

参考文献: [https://arxiv.org/abs/2105.15183](https://arxiv.org/abs/2105.15183) （セクション2 + 付録Aの終わり）。

# フィールド

  * `f`: `x` に関して最小化する関数 `f(x, θ)`
  * `f_grad1`: `x` に関する `f` の勾配 `∇ₓf(x, θ)`
  * `lmo`: 線形最小化オラクル `θ -> argmin_{x ∈ C} θᵀx` [FrankWolfe.jl] から、凸集合 `C` を暗黙的に定義します
  * `alg`: [FrankWolfe.jl](https://github.com/ZIB-IOL/FrankWolfe.jl) からの最適化アルゴリズム
  * `implicit`: [ImplicitDifferentiation.jl](https://github.com/gdalle/ImplicitDifferentiation.jl) からの暗黙的関数
