```julia
projectXrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

`state`の`qubit`をX軸に沿って投影し、必要に応じて位相をランダム化します。

[`project!`](@ref)の簡略版です。

関連項目: [`project!`](@ref), [`projectX!`](@ref), [`projectZrand!`](@ref), [`projectYrand!`](@ref)
