```
 hreval(Ahr::HarmonicArray, t; ntrunc, exact = true) -> A::Matrix
```

Evaluate the harmonic array `Ahr` representing a continuous-time  time periodic matrix `A(t)` for a time value `t`.  For a real value `t`, if `exact = true (default)` an exact evaluation is computed, while for `exact = false`,  a linear interpolation based approximation is computed (potentially more accurate in intersample points). The keyword argument `ntrunc` specifies the number of harmonics to be used for the evaluation  (default: maximum possible number). 
