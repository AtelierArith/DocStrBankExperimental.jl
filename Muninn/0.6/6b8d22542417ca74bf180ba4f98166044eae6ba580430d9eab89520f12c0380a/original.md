```
TImodel1(params::Sleipnir.Parameters; DDF::F = 7.0/1000.0, acc_factor::F = 1.0/1000.0) where {F <: AbstractFloat}
```

Create a temperature index model with one degree-day factor (DDF) with the given parameters.

# Arguments

  * `params::Sleipnir.Parameters`: The simulation parameters.
  * `DDF::F`: Degree-day factor (default is 7.0/1000.0).
  * `acc_factor::F`: Accumulation factor (default is 1.0/1000.0).

# Returns

  * `TI1_model`: An instance of TImodel1 with the specified parameters.
