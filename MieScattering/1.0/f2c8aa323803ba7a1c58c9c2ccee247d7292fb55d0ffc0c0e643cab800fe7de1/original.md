```
mie_phase_matrix(m, x, μ; norm=:albedo)
```

Calculate the phase scattering matrix.

The units are $sr^{-1}$. The phase scattering matrix is computed from the scattering amplitude functions, according to equations 5.2.105-6 in K. N. Liou (**2002**) - *An Introduction to Atmospheric Radiation*, Second Edition.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `μ`: the angles, cos(theta), at which to calculate the phase scattering matrix

# Output

  * `p`: The phase scattering matrix [$sr^{-1}$]
