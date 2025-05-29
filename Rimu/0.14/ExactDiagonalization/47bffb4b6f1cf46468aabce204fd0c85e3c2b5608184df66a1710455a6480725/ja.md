```
ArpackSolver(; kwargs...)
```

スパース行列をインスタンス化した後に[`ExactDiagonalizationProblem`](@ref)を解くためのアルゴリズムです。エルミート問題にはランツコス法を、非エルミート問題にはアーノルディ法を使用し、Arpack Fortranライブラリを利用します。これは[`KrylovKitSolver(; matrix_free=true)`](@ref)よりも速いですが、より多くのメモリを必要とし、行列がメモリに収まる場合にのみ有用です。

`kwargs`は関数[`Arpack.eigs()`](https://arpack.julialinearalgebra.org/stable/eigs/)に渡されます。

他に[`ExactDiagonalizationProblem`](@ref)、[`solve`](@ref solve(::ExactDiagonalizationProblem))も参照してください。

!!! note
    `using Arpack`でArpack.jlパッケージをロードする必要があります。

