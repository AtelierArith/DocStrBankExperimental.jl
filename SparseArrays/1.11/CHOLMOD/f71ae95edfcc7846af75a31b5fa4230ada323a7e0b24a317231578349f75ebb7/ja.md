```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

与えられた `LDLt` または `LLt` 因子分解 `F` の `A + C*C'` の `LDLt` 因子分解を取得します。

返される因子は常に `LDLt` 因子分解です。

他にも [`lowrankdowndate!`](@ref)、[`lowrankupdate`](@ref)、[`lowrankupdate!`](@ref) を参照してください。
