```
update_noise(c::AbstractCircuit, noise_param::AbstractNoiseParameters)
update_noise(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}})
```

Returns a copy of `c` where the circuit has been updated with noise generated according to `noise_param`, or the gate probabilities `gate_probabilities`.
