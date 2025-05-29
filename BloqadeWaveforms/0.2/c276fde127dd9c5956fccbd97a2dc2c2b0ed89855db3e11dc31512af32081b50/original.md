```
sample_values(wf::Waveform, clocks; offset::Real = zero(eltype(wf)))
sample_values(wf::Waveform; offset::Real = zero(eltype(wf)), dt::Real = 1e-3)
```

Samples of waveform `wf` values obtainable by either providing an iterable `clocks` containing exact time values to sample from or providing `offset` and `dt` values  which specify the offset to add to the beginning and end of the waveforms time span and  the step between time values. 

See also [`sample_clock`](@ref)

```jldoctest; setup:=using(using BloqadeWaveforms)
julia> wf = linear_ramp(duration=0.5, start_value=0.0, stop_value=2π*1.0);

julia> sample_values(wf,0.0:0.1:0.5) # sample waveform values from range
6-element Vector{Float64}:
 0.0
 1.2566370614359172
 2.5132741228718345
 3.7699111843077517
 5.026548245743669
 6.283185307179586

julia> sample_values(wf; dt=5e-2) #5e-2 time gap between each sampled valued
11-element Vector{Float64}:
 0.0
 0.6283185307179586
 1.2566370614359172
 1.8849555921538759
 2.5132741228718345
 3.141592653589793
 3.7699111843077517
 4.39822971502571
 5.026548245743669
 5.654866776461628
 6.283185307179586

```
