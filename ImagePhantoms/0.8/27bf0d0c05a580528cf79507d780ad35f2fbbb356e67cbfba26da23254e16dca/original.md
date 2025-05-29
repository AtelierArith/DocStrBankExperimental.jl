```
mri_spectra(fx, fy, oa::Array{<:Object2d}, fit::NamedTuple)
```

Version of `spectrum` suitable for parallel MRI with sensitivity maps that were fit previously using `mri_smap_fit`. Returns a Vector of `ncoil` kspace data Vectors of dimension `length(fx)`
