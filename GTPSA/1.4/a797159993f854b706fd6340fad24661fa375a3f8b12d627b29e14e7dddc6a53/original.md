```
vars(use::Union{Descriptor,TPS}=GTPSA.desc_current)
```

Returns a vector of `TPS`s corresponding to the variables for the  `Descriptor` specified by `use`. Default value is `GTPSA.desc_current`.

### Input

  * `use` – (Optional) Specify which `Descriptor` to use, default is `GTPSA.desc_current`

### Output

  * `x`   – `Vector` containing unit `TPS{Float64}`s corresponding to each variable
