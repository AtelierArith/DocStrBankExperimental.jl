```
signalTypeDAC!(rp::RedPitaya, channel, value)
```

Return the signalType of composite waveform for `channel`.

See [`signalTypeDAC!`](@ref).

# Examples

```julia
julia> signalTypeDAC!(rp, 1, SINE);
true

julia> signalTypeDAC(rp, 1)
SINE
```
