```
spin_weighted_spheroidal_eigenvalue(s::Int, l::Int, m::Int, c; N::Int=-1)
```

Compute the eigenvalue of the spin-weighted spheroidal harmonic with spin weight `s`, harmonic index `l`, azimuthal index `m`, and spheroidicity `c` ($c = a\omega$).

The optional argument `N` specifies the number of terms to use in the spectral decomposition. The default value is `N=-1`, which indicates that a suitable value of `N` will be determined automatically.

This function is simply a wrapper to `Teukolsky_lambda_const` for backward compatbility.
