```
serverMode!(rp::RedPitaya, mode::ServerMode)
```

Set the mode of the server. Valid values are "`CONFIGURATION`" and "`ACQUISITION`".

# Examples

```julia
julia> serverMode!(rp, ACQUISITION);
true

julia> serverMode(rp)
ACQUISITION
```
