```
sample_clock(wf::Waveform; offset::Real = zero(eltype(wf)), dt::Real = 1e-3)
```

Generates range of time values based on `wf`'s duration  with `dt` time between each time value along with `offset` time added to the beginning and end of the waveform's time span.

See also [`sample_values`](@ref)

```jldoctest; setup=:(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=2π*2.2); # create a waveform

julia> sample_clock(wf;) # range from 0.0 to 2.0 with step of 0.001 (default arg)
0.0:0.001:2.0

julia> sample_clock(wf; offset=0.1) # offset beginning and end by 0.1
0.1:0.001:2.1

julia> sample_clock(wf; dt = 2e-3) # set step size of 2e-3
0.0:0.002:2.0
```
