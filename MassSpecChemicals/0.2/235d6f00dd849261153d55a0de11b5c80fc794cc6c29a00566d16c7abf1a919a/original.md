```
@ri_str -> RealInterval
```

Create a `RealInterval` by mathematical real interval notation.

# Examples

```julia
julia> interval = ri"[4, 7)";

julia> 4 in interval
true

julia> 7 in interval
false
```
