```
piecewise_constant_interpolate(wf::Waveform; min_step::Real=0.0, atol::Real = 1.0e-5)
```

Converts `wf` to a [`piecewise_constant`](@ref) waveform subject to `min_step`  (the smallest allowable time step) and tolerance `atol`.
