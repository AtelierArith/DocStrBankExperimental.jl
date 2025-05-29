```
 tvmeval(Ahr::HarmonicArray, t; ntrunc, exact = true) -> A::Vector{Matrix}
```

Evaluate the time response of a harmonic array.

For the harmonic array `Ahr` representing representing a continuous-time  time periodic matrix `A(t)` and the vector of time values `t`,  `A[i] = A(t[i])` is computed for each time value `t[i]`.  If `exact = true (default)` an exact evaluation is computed, while for `exact = false`,  a linear interpolation based approximation is computed  (potentially more accurate in intersample points). The keyword argument `ntrunc` specifies the number of harmonics to be used for evaluation  (default: maximum possible number of harmonics). 
