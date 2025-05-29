```
emission_limit(modeltype::EnergyModel)
emission_limit(modeltype, p::ResourceEmit)
emission_limit(modeltype, p::ResourceEmit, t_inv::TS.AbstractStrategicPeriod)
```

Returns the emission limit of EnergyModel `model` as dictionary with `TimeProfile`s for each [`ResourceEmit`](@ref), as `TimeProfile` for [`ResourceEmit`](@ref) `p` or, in strategic period `t_inv` for [`ResourceEmit`](@ref) `p`.
