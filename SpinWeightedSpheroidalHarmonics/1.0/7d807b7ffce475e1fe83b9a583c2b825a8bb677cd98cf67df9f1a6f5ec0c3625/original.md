```
spin_weighted_spheroidal_harmonic(s::Int, l::Int, m::Int, c; N::Int=-1, method="auto")
```

Construct the spectral decomposition of this spin-weighted spheroidal harmonic of  spin weight `s`, harmonic index `l`, azimuthal index `m`, and spheroidicity `c` ($c = a\omega$)  using `N` spin-weighted *spherical* harmonics.

Note that the default value for `N=-1` indicates that a suitable value of `N` will be determined automatically.

Return a SpinWeightedSpheroidalHarmonicFunction object that can be evaluated at any point.

By default, the method to compute the value for the underlying spin-weighted spherical harmonics  is chosen automatically based on the value of the harmonic index `l`. When `l < 30`, the direct evaluation method (`method="direct"`) is used where we evaluate the exact analytical solution as shown in Eq. (A8). However, the prefactor in each term of the sum can be very large and thus cause overflow, while the sum itself is finite (of order 1 actually). Therefore, when `l >= 30`, the Chebyshev pseudo-spectral method (`method="chebyshev"`) is used instead.
