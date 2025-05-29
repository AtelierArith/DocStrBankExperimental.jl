```julia
projectrand!(
    state,
    pauli
) -> Tuple{QuantumClifford.Register, Any}

```

`state`上で`pauli`演算子を測定し、必要に応じて位相をランダム化します。

[`project!`](@ref)の簡略化バージョンです。

関連情報: [`project!`](@ref), [`projectXrand!`](@ref), [`projectZrand!`](@ref), [`projectYrand!`](@ref)
