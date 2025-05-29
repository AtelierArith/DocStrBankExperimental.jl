```
clear_uni_integral_defaults()::Nothing
```

Clears and resets the keyword argument defaults for univariate integrals to their  default state. 

**Example**

```julia-repl
julia> uni_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Quadrature()

julia> clear_uni_integral_defaults()

julia> uni_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()
```
