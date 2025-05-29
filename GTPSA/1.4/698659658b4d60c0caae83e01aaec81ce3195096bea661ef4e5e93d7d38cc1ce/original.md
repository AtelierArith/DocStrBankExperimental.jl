```
complexparams(use::Union{Descriptor,TPS}=GTPSA.desc_current)
```

Returns a vector of `ComplexTPS64`s corresponding to the parameters for the  `Descriptor` specified by `use`. Default value is `GTPSA.desc_current`.

### Input

  * `use` – (Optional) Specify which `Descriptor` to use, default is `GTPSA.desc_current`

### Output

  * `x`   – `Vector` containing unit `ComplexTPS64`s corresponding to each parameters
