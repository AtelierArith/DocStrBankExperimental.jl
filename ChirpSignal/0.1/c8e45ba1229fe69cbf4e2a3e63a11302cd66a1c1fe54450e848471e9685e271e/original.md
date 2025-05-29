```
chirp(T, fs, f::Function; phase=0.0) -> Array{Float64,1}
```

Function customizable chirp swept-frequency sine generator.

# Arguments

  * `T`     : signal's length in second
  * `fs`    : sampling rate
  * `f`     : function that defines how the frequency changes vs time
  * `phase` : phase of the chirp sigal, like sin(wt + phase)
