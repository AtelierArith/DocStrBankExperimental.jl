```
spin_weighted_spherical_harmonic(s::Int, l::Int, m::Int; method="auto")
```

Construct the spin-weighted spherical harmonic of  spin weight `s`, harmonic index `l`, and azimuthal index `m`.

Return a SpinWeightedSphericalHarmonicFunction object that can be evaluated at any point.

By default, the method to compute the value is chosen automatically based on the value of the harmonic index `l`. When `l < 30`, the direct evaluation method (`method="direct"`) is used where we evaluate the exact analytical solution as shown in Eq. (A8). However, the prefactor in each term of the sum can be very large and thus cause overflow, while the sum itself is finite (of order 1 actually). Therefore, when `l >= 30`, the Chebyshev pseudo-spectral method (`method="chebyshev"`) is used instead.
