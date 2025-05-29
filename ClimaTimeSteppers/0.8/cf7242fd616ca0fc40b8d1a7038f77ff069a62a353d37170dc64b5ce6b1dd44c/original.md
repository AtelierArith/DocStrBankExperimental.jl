```
ForcingTerm
```

Computes the value of `rtol[n]` for a Newton-Krylov method. This is done by calling `get_rtol!(::ForcingTerm, cache, f, n)`, which returns `rtol[n]`. The `cache` can be obtained with `allocate_cache(::ForcingTerm, x_prototype)`, where `x_prototype` is `similar` to `f`.

For a detailed discussion of forcing terms and their convergence guarantees, see "Choosing the Forcing Terms in an Inexact Newton Method" by S.C. Eisenstat and H.F. Walker (http://softlib.rice.edu/pub/CRPC-TRs/reports/CRPC-TR94463.pdf).
