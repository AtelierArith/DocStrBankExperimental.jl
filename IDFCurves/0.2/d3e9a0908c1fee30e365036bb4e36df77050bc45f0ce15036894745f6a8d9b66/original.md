```
initialize(::Type{<:GeneralScaling}, data::IDFdata, d₀::Real)
```

Initialize a vector of parameters for the GeneralScaling marginal model with reference duration d₀, adapted to the data. The initialization is the same as for the SImpleScaling model. δ is initialized at (close to) 0 as a default.
