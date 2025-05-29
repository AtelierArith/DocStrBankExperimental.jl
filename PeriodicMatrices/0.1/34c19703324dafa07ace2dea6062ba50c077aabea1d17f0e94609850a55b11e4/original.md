```
 hreval(Ahr::HarmonicArray, t; ntrunc, exact = true) -> A::Matrix
```

Evaluate the harmonic array `Ahr` representing a continuous-time  time periodic matrix `A(t)` for a symbolic time value `t`.  A symbolic evaluation of `A(t)` is performed (see also [`hr2psm`](@ref)) The keyword argument `ntrunc` specifies the number of harmonics to be used for the evaluation  (default: maximum possible number). 
