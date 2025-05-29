```
phaseDAC(rp::RedPitaya, channel, component)
```

Return the phase of composite waveform `component` for `channel`.

See [`phaseDAC!`](@ref).

# Examples

```julia
julia> phaseDAC!(rp, 1, 1, 0.0);
true

julia> phaseDAC(rp, 1, 0.0)
0.0
```
