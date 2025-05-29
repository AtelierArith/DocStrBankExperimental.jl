```
lcgfp = lefschetz_gfp_conversion(lc::LefschetzComplex, p::Int)
```

Convert a Lefschetz complex to the same complex over a finite field.

It is expected that the boundary matrix of the given Lefschetz complex `lc` is defined over the rationals, and that the target characteristic `p` is a prime.
