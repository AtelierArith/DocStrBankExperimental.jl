```
phaseDAC!(rp::RedPitaya, channel, component, value)
```

Set the phase of composite waveform `component` for `channel`. Return `true` if the command was successful.

See [`phaseDAC`](@ref).

# Examples

```julia
julia> phaseDAC!(rp, 1, 1, 0.0);
true

julia> phaseDAC(rp, 1, 0.0)
0.0
```
