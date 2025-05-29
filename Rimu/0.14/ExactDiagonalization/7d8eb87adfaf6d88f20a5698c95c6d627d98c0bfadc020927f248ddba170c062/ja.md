```
KrylovKitSolver(matrix_free::Bool; kwargs...)
KrylovKitSolver(; matrix_free = false, kwargs...)
```

KrylovKit.jlパッケージを使用して、いくつかの固有値とベクトルを見つけるために大規模な [`ExactDiagonalizationProblem`](@ref) を解くアルゴリズム。エルミート行列にはランチョス法が使用され、非エルミート行列にはアーノルディ法が使用されます。

# 引数

  * `matrix_free = false`: 行列フリーアルゴリズムを使用するかどうか。`false` の場合、スパース行列がインスタンス化されます。これは通常、より小さな行列に対しては高速で推奨されますが、より多くのメモリを必要とします。`true` の場合、行列はインスタンス化されず、メモリに収まらない大きな行列に対して便利です。計算は、[`PDVec`](@ref) を利用して、スレッドとMPIを使用して並列化されます。
  * `kwargs`: 追加のキーワード引数は、関数 [`KrylovKit.eigsolve()`](https://jutho.github.io/KrylovKit.jl/stable/man/eig/#KrylovKit.eigsolve) に渡されます。

他に [`ExactDiagonalizationProblem`](@ref)、[`solve`](@ref solve(::ExactDiagonalizationProblem)) も参照してください。

!!! note
    `using KrylovKit` でKrylovKit.jlパッケージをロードする必要があります。

