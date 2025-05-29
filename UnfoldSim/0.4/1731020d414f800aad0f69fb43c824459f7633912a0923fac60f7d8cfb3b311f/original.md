```
p100(; sfreq = 100)
```

Generate a Hanning window mimicking a P100 EEG component with a peak at 100ms and a width of 100ms.

# Keyword arguments

  * `sfreq = 100`: Sampling frequency in Hz.

# Returns

  * `Vector`: Contains a shifted (i.e. zero-padded) hanning window.

# Examples

```julia-repl
julia> p100(; sfreq = 200)
30-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 ⋮
 0.37725725642960045
 0.22652592093878665
 0.10542974530180327
 0.02709137914968268
 0.0
```

See also [`p300`](@ref), [`n170`](@ref), [`n400`](@ref), [`hanning`](@ref).
