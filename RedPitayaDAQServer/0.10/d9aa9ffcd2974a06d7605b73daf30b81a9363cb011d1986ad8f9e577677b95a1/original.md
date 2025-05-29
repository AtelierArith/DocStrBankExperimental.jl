```
amplitudeDAC(rp::RedPitaya, channel, component)
```

Return the amplitude of composite waveform `component` for `channel`.

See [`amplitudeDAC!`](@ref).

# Examples

```julia
julia> amplitudeDAC!(rp, 1, 1, 0.5);
true

julia> amplitudeDAC(rp, 1, 1)
0.5
```
