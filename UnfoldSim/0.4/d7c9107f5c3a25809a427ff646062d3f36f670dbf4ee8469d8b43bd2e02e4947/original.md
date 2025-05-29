```
p300(; sfreq = 100)
```

Generate a Hanning window mimicking a P300 EEG component with a peak at 300ms and a width of 300ms.

# Keyword arguments

  * `sfreq = 100`: Sampling frequency in Hz.

# Returns

  * `Vector`: Contains a shifted (i.e. zero-padded) hanning window.

# Examples

```julia-repl
julia> p300(; sfreq = 150)
67-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 ⋮
 0.07937323358440934
 0.04518400232274078
 0.02025351319275137
 0.005089279059533658
 0.0
```

See also [`p100`](@ref), [`n170`](@ref), [`n400`](@ref), [`hanning`](@ref).
