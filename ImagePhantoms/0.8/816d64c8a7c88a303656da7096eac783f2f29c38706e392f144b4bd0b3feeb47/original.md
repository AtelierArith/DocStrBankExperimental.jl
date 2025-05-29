```
spectrum(ob::Object2d, coefs::AbstractVector, f::)
```

Version of `spectrum(ob)` suitable for parallel MRI with sensitivity maps that were fit previously using `mri_smap_fit` for a single coil with fit coefficients `coefs` and frequencies `f` (array of tuples).
