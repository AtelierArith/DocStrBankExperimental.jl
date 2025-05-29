```
offsetDAC!(rp::RedPitaya, channel, value)
```

Set the offset for `channel`. Return `true` if the command was successful.

See [`offsetDAC`](@ref).

# Examples

```julia
julia> offsetDAC!(rp, 1, 0.2);
true

julia> offsetDAC(rp, 1)
0.2
```
