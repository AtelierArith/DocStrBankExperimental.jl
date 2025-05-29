```julia
projectYrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

状態の `qubit` を Y 軸に沿って投影し、必要に応じて位相をランダム化します。

[`project!`](@ref) の簡略版です。

参照: [`project!`](@ref), [`projectY!`](@ref), [`projectXrand!`](@ref), [`projectZrand!`](@ref)
