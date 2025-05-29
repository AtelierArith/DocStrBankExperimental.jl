```
c = vee(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, X)
vee!(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, c, X)
```

接続ベクトルをリー代数から座標ベクトル `c` にマッピングする vee マップ $(⋅)^{\vee}: \mathfrak g →  ℝ^{n^2-1}$ を計算します。

リー代数 $𝔤$ の [`SpecialLinearGroup`](@ref)`(n)` における公式は、$X ∈ ℝ^{n×n}$ をベクトルに再形成し、最後のエントリを省略することによって与えられます。なぜなら、$X$ はトレースゼロである必要があるため、最後のエントリは再構築できます。

これは `c` のインプレースで計算できます。
