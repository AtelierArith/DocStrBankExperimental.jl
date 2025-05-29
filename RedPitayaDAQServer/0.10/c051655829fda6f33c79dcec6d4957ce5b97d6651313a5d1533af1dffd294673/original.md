```
amplitudeDAC!(rp::RedPitaya, channel, component, value)
```

Set the amplitude of composite waveform `component` for `channel`. Return `true` if the command was successful.

See [`amplitudeDAC`](@ref).

# Examples

```julia
julia> amplitudeDAC!(rp, 1, 1, 0.5);
true

julia> amplitudeDAC(rp, 1, 1)
0.5
```
