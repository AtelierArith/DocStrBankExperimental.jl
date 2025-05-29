```
emission_price(modeltype::EnergyModel)
emission_price(modeltype, p::ResourceEmit)
emission_price(modeltype, p::ResourceEmit, t_inv::TS.TimePeriod)
```

Returns the emission price of EnergyModel `model` as dictionary with `TimeProfile`s for each [`ResourceEmit`](@ref), as `TimeProfile` for [`ResourceEmit`](@ref) `p` or, in operational period `t` for [`ResourceEmit`](@ref) `p`.
