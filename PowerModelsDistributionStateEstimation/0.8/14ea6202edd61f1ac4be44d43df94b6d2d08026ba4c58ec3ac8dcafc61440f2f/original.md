```
update_load_bounds!(data::Dict; p_min::Float64=0.0, p_max::Float64=Inf, q_min::Float64=-Inf, q_max::Float64=Inf)
```

Function that allows to automatically set upper (p*max, q*max) and lower (p*min, q*min) active and reactive power bounds for all loads. It assumes that there are at most four active phases and all have the same bounds.
