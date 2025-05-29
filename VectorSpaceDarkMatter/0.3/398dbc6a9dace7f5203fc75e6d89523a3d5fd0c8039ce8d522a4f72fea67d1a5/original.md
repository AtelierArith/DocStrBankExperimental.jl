```
rate(R, mcK::McalK)
```

Calculates the rate for a given partial rate matrix `mcK` and rotation `R` given as a quaternion or rotor (to use other rotations, see `Quaternionic.jl`'s conversion methods). `R` can also be a vector of quaternions or rotors.

The maximum $\ell$ that is used is the minimum of the specified `ell_max` and the maximum $\ell$ for each of `pfv` and `pfq`.

Measurements are not supported here (yet).
