```
loop_update!(model, param::Parameter)
loop_update!(model, T::Real,
             Jz::AbstractArray,
             Jxy::AbstractArray,
             Gamma:AbstractArray)
```

Updates spin configuration by loop algorithm  under the temperature `T = param["T"]` and coupling constants `Jz, Jxy` and transverse field `Gamma`
