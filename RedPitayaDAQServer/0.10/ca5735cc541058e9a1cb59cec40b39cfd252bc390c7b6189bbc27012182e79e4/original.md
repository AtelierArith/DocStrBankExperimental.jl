```
frequencyDAC!(rp::RedPitaya, channel, component, value)
```

Set the frequency of composite waveform `component` for `channel`. Return `true` if the command was successful.

See [`frequencyDAC`](@ref).

# Examples

```julia
julia> frequencyDAC!(rp, 1, 1, 2400);
true

julia> frequencyDAC(rp, 1, 1)
2400
```
