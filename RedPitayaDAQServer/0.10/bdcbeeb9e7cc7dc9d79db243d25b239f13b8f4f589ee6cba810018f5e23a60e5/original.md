```
offsetDAC(rp::RedPitaya, channel)
```

Return the offset for `channel`.

See [`offsetDAC!`](@ref).

# Examples

```julia
julia> offsetDAC!(rp, 1, 0.2);
true

julia> offsetDAC(rp, 1)
0.2
```
