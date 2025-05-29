```
TImodel2{F <: AbstractFloat}
```

A type representing a temperature-index model with parameters for snow and ice degree-day factors, and an accumulation factor.

# Keyword arguments

  * `DDF_snow::F`: Degree-day factor for snow, which determines the melt rate of snow per degree above the melting point.
  * `DDF_ice::F`: Degree-day factor for ice, which determines the melt rate of ice per degree above the melting point.
  * `acc_factor::F`: Accumulation factor, which scales the accumulation of snow.

# Type Parameters

  * `F`: A subtype of `AbstractFloat`, representing the numeric type used for the model parameters.
