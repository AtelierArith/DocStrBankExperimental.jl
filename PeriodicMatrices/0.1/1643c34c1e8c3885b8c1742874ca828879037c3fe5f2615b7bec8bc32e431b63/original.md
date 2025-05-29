```
 hr2psm(Ahr::HarmonicArray, nrange) -> A::Matrix{Num}
```

Convert a range of harmonic components `nrange` of the harmonic array `Ahr` to a symbolic matrix `A`.  The default range is `nrange = 0:n`, where `n` is the order of the maximum harmonics.  
