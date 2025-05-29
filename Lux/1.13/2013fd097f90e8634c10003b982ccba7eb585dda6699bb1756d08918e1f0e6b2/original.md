```
bf16(m)
```

Converts the `eltype` of `m` *floating point* values to `BFloat16`. To avoid recursion into structs mark them with `Functors.@leaf`.

!!! warning
    `BFloat16s.jl` needs to be loaded before using this function.


!!! tip "Support for `BFloat16`"
    Most Lux operations aren't optimized for `BFloat16` yet. Instead this is meant to be used together with `Reactant.@compile`.

