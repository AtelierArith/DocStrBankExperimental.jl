```
AbstractState_set_cubic_alpha_C(handle::Clong, i::Integer, parameter::AbstractString, c1::Real, c2::Real, c3::Real)
```

Set cubic's alpha function parameters.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `i`: indice of the fluid the parameter should be applied too (for mixtures)
  * `parameter`: the string specifying the alpha function to use, e.g. "TWU" for the Twu or "MC" for Mathias-Copeman alpha function.
  * `c1`: the first parameter for the alpha function
  * `c2`: the second parameter for the alpha function
  * `c3`: the third parameter for the alpha function
