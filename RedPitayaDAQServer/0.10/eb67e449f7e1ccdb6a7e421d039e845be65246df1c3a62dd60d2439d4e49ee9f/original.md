```
frequencyDAC(rp::RedPitaya, channel, component)
```

Return the frequency of composite waveform `component` for `channel`.

See [`frequencyDAC!`](@ref).

# Examples

```julia
julia> frequencyDAC!(rp, 1, 1, 2400);
true

julia> frequencyDAC(rp, 1, 1)
2400
```
