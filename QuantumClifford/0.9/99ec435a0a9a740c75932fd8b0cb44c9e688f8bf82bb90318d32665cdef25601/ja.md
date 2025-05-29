```julia
projectZrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

`state`の`qubit`をZ軸に沿って射影し、必要に応じて位相をランダム化します。

[`project!`](@ref)の簡易版です。

関連項目: [`project!`](@ref), [`projectZ!`](@ref), [`projectXrand!`](@ref), [`projectYrand!`](@ref)
