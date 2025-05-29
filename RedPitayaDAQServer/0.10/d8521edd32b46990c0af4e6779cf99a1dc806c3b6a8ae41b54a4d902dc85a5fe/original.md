```
signalTypeDAC!(rp::RedPitaya, channel, value)
```

Set the signalType of composite waveform for `channel`. Return `true` if the command was successful.

See [`signalTypeDAC`](@ref).

# Examples

```julia
julia> signalTypeDAC!(rp, 1, SINE);
true

julia> signalTypeDAC(rp, 1)
SINE
```
