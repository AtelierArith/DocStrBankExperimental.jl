```
StatsBase.confint(lmm::LMM{T}; level::Real=0.95, ddf::Symbol = :satter) where T
```

Confidece interval for coefficients.

ddf = :satter/:residual

$$
CI_{U/L} = β ± SE * t_{ddf, 1-α/2}
$$

See also: [`dof_satter`](@ref), [`dof_residual`](@ref)
