```
ez_mie(m, d, λ0, n_env = 1.0)
```

Calculate the efficiencies of a sphere.

# Parameters

  * `m`: the complex index of refraction of the sphere    [-]
  * `d`: the diameter of the sphere                       [same units as lambda0]
  * `λ0`: wavelength in a vacuum                          [same units as d]
  * `n_env`: real index of medium around sphere, optional.
  * `use_threads` (optional): Flag whether to use threads (default: true)

# Output

  * `qext`: the total extinction efficiency                  [-]
  * `qsca`: the scattering efficiency                        [-]
  * `qback`: the backscatter efficiency                      [-]
  * `g`: the average cosine of the scattering phase function [-]
