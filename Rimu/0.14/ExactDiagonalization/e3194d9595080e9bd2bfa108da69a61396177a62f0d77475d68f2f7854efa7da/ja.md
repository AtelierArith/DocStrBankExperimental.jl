```
LinearAlgebraSolver(; kwargs...)
```

[`ExactDiagonalizationProblem`](@ref)を解くためのアルゴリズムで、`LinearAlgebra`標準ライブラリの密行列固有値ソルバーを使用します。これは小さな行列にのみ適しています。

`kwargs`は関数[`LinearAlgebra.eigen`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigen)に渡されます。

# キーワード引数

  * `permute = true`: 対角化の前に行列を置換するかどうか。
  * `scale = true`: 対角化の前に行列をスケーリングするかどうか。
  * `sortby`: 固有値のソート順。

他に[`ExactDiagonalizationProblem`](@ref)、[`solve`](@ref solve(::ExactDiagonalizationProblem))も参照してください。
