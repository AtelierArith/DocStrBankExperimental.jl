```
XPRS_ge_setarchconsistency(consistent)::Nothing
```

Sets whether to force the same execution path on various CPU architecture extensions, in particular (pre-)AVX and AVX2.

# Arguments

  * `consistent::Integer`: Whether to force the same execution path: 0Do not force the same execution path (default behavior); 1Force the same execution path.

See also the documentation of the correponding function [XPRS*ge*setarchconsistency](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_ge_setarchconsistency.html) in the C API.
