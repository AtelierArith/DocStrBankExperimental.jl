```
serverMode!(rp::RedPitaya, mode::ServerMode)
```

Set the mode of the server.

# Examples

```julia
julia> serverMode!(rp, ACQUISITION);
true

julia> serverMode(rp)
ACQUISITION
```
