```
StatsBase.confint(lmm::LMM{T}; level::Real=0.95, ddf::Symbol = :satter) where T
```

係数の信頼区間。

ddf = :satter/:residual

$$
CI_{U/L} = β ± SE * t_{ddf, 1-α/2}
$$

参照: [`dof_satter`](@ref), [`dof_residual`](@ref)
