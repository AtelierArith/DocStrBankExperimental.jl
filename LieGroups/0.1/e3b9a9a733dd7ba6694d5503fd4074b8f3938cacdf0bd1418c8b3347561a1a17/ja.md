```
X = hat(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, c)
hat!(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, X, c)
```

ベクトルの座標 `c` をリー代数の接ベクトルに変換するハット写像 $(⋅)^{\wedge} : ℝ^{n^2-1} → 𝔤$ を計算します。

[`SpecialLinearGroup`](@ref)`(n)` のリー代数 $𝔤$ における公式は、$c ∈ ℝ^{n^2-1}$ を最終エントリ `X[n,n]` がゼロに初期化された $n$-by-$n$ 行列 $X$ に再形成し、その後この初期行列のトレースに設定されます。

これは `X` のインプレースで計算できます。
