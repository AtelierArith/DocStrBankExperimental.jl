```
initialize(::Type{<:DependentScalingModel}, data::IDFdata, d₀::Real)
```

Initialize a vector of parameters for the DependentScalingmodel adapted to the data. The initialization is done independently for the marginal scaling model and the correlation structure.
