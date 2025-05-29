```
evolve!(itoprocesses::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}}, stochastics::Union{Dict{Symbol,R},Dict{Symbol,Real}}, new_time::Real) where R<:Real
```

Evolve the `ItoProcess` forward. This changes the time (`t0`) as well as the `value`.

### Inputs

  * `itoprocesses` - A `Dict` of `ItoProcess`es
  * `stochastic` - A `Dict` of draws from the `ItoIntegral`.
  * `new_time` - The new time.

### Return

Nothing. It changes the input `ItoProcess`
