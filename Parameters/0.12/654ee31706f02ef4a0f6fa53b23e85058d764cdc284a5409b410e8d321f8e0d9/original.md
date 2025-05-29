Macro which allows default values for field types and a few other features.

Basic usage:

```julia
@with_kw struct MM{R}
    r::R = 1000.
    a::Int = 4
end
```

For more details see manual.
