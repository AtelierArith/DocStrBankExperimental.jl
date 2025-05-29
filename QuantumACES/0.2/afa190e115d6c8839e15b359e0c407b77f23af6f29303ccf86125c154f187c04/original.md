```
update_noise(d::Design, noise_param::AbstractNoiseParameters)
update_noise(d::Design, gate_probabilities::Dict{Gate, Vector{Float64}})
```

Returns a copy of the design `d` where the circuit has been updated with noise generated according to `noise_param`, or the gate probabilities `gate_probabilities`.
