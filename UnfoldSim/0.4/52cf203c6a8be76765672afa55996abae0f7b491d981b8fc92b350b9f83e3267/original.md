```
n400(; sfreq = 100)
```

Generate a Hanning window mimicking an N400 EEG component with a negative (!) peak at 400ms and a width of 400ms.

# Keyword arguments

  * `sfreq = 100`: Sampling frequency in Hz.

# Returns

  * `Vector`: Contains a shifted (i.e. zero-padded) hanning window.

# Examples

```julia-repl
julia> n400(; sfreq = 250)
150-element Vector{Float64}:
 -0.0
 -0.0
 -0.0
 -0.0
 -0.0
  ⋮
 -0.016025649301821876
 -0.009035651368646647
 -0.00402259358460233
 -0.0010066617640578368
 -0.0
```

See also [`p100`](@ref), [`p300`](@ref), [`n170`](@ref), [`hanning`](@ref).
