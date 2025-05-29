```
n170(; sfreq = 100)
```

Generate a Hanning window mimicking an N170 EEG component with a negative (!) peak at 170ms and a width of 150ms.

# Keyword arguments

  * `sfreq = 100`: Sampling frequency in Hz.

# Returns

  * `Vector`: Contains a shifted (i.e. zero-padded) hanning window.

# Examples

```julia-repl
julia> n170(; sfreq = 120)
28-element Vector{Float64}:
 -0.0
 -0.0
 -0.0
 -0.0
 -0.0
  ⋮
 -0.45386582026834904
 -0.2771308221117309
 -0.1304955413896705
 -0.03376388529782215
 -0.0
```

See also [`p100`](@ref), [`p300`](@ref), [`n400`](@ref), [`hanning`](@ref).
