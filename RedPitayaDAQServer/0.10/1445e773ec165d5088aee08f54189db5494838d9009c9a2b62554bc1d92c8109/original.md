```
decimation!(rp::RedPitaya, dec)
```

Set the decimation of the RedPitaya. Return `true` if the command was successful.

# Examples

```julia
julia> decimation!(rp, 8)
true

julia> decimation(rp)
8
```
