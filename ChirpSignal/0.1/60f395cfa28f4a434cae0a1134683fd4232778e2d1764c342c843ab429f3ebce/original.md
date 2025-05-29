```
chirp(T, fs, fl, fh; method="linear", phase=0.0) -> Array{Float64,1}
```

Chirp Swept-frequency sine generator.

# Arguments

  * `T`     : signal's length in second
  * `fs`    : sampling rate
  * `fl`    : lower frequency at the ending time step, fl <= fs
  * `fh`   : higher frequency at the ending time step, fh <= fs
  * `phase` : phase of the chirp sigal, like sin(wt + phase)
  * `method`: available methods are 'linear','quadratic','exponential' and 'logarithmic'; the default is 'linear'
