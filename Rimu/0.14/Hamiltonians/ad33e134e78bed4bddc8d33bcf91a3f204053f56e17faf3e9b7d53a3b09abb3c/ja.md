```
MatrixHamiltonian(
    mat::AbstractMatrix{T};
    starting_address::Int = starting_address(mat)
) <: AbstractHamiltonian{T}
```

抽象行列 `mat` を [`AbstractHamiltonian`](@ref) オブジェクトとしてラップします。これは [`ProjectorMonteCarloProblem()`](@ref) および [`DVec`](@ref) の確率的手法で動作します。オプションで、有効なインデックスを [`starting_address`](@ref) として提供できます。

型 `AbstractSparseMatrixCSC` のスパース行列に対して特化したメソッドが実装されています。行列 `mat` には 1 ベースのインデックスが必要です。
