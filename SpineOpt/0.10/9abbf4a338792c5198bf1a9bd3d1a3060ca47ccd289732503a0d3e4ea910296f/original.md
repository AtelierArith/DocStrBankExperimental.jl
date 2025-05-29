```
roll_temporal_structure!(m[, window_number=1]; rev=false)
```

Roll the temporal structure of given SpineOpt model forward a period of time equal to the value of the `roll_forward` parameter. If `roll_forward` is an array, then `window_number` can be given either as an `Integer` or a `UnitRange` indicating the position or successive positions in that array.

If `rev` is `true`, then the structure is rolled backwards instead of forward.
