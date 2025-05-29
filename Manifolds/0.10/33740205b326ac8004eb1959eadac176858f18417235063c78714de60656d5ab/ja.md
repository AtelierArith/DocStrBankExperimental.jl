```
rand(::MultinomialDoubleStochastic; vector_at=nothing, σ::Real=1.0, kwargs...)
```

[`MultinomialDoubleStochastic`](@ref) 多様体上のランダム点を生成するか、`vector_at` が `nothing` でない場合はその点での接ベクトルを生成します。

`n×n` は [`MultinomialDoubleStochastic`](@ref) の行列次元を示します。

`vector_at` が `nothing` の場合、正のエントリを持つランダム行列 `rand(n,n)` を生成し、それを多様体に射影することで行います。`kwargs...` はこの射影に渡されます。

`vector_at` が `nothing` でない場合、周囲空間内のランダム行列が生成され、それを接空間に射影します。
