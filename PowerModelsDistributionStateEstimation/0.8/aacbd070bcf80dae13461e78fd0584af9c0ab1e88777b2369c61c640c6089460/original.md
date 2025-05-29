```
update_generator_bounds!(data; p_min, p_max, q_min, q_max)
```

Function that allows to automatically set upper (p*max, q*max) and lower (p*min, q*min) active and reactive power bounds for all generators. It assumes that there are at most  four active phases and all have the same bounds.
