```
set_default(; kwargs...)
```

Set default kwarg values for latexify. 

This works for all keyword arguments except `:env`. It is additive such that if you call it multiple times, defaults will be added or replaced, but not reset.

Example: 

```julia
set_default(mult_symbol = "", transpose = true)
```

To reset the defaults that you have set, use `reset_default`. To see your specified defaults, use `get_default`.
