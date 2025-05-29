```
build_lut(f, coords::Pair{Symbol,<:Union{Number,AbstractVector}}...; f_kwargs...)
```

Builds an n-dimensional lookup table `LUT` by invoking `f` on the given `coords`. `f` should be a function which accepts keyword arguments matching `coords` as well as any additional constant keyword arguments `f_kwargs`.

Example:

```julia
f(; x=1.0, y=1.0) = x + y
lut = build_lut(f, :x => -10.0:10.0, :y=-10.0:10.0)
lut(; x=2.2, y=1.5)
# output
3.7
```
