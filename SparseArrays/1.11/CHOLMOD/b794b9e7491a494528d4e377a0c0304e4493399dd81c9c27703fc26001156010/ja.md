```
lowrankupdate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

与えられた `A` の `LDLt` または `LLt` 因子分解 `F` に対して、`A + C*C'` の `LDLt` 因子分解を取得します。

返される因子は常に `LDLt` 因子分解です。

他にも [`lowrankupdate!`](@ref)、[`lowrankdowndate`](@ref)、[`lowrankdowndate!`](@ref) を参照してください。
