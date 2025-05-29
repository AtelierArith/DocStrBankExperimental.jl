```
ez_intensities(m, d, λ0, μ, n_env = 1.0, norm = :albedo)
```

Return the scattered intensities from a sphere. These are the scattered intensities in a plane that is parallel (ipar) and perpendicular (iper) to the field of the incident plane wave. The scattered intensity is normalized such that the integral of the unpolarized intensity over 4𝜋 steradians is equal to the single scattering albedo.  The scattered intensity has units of inverse steradians [1/sr]. The unpolarized scattering is the average of the two scattered intensities.

# Parameters

  * `m`: the complex index of refraction of the sphere    [-]
  * `d`: the diameter of the sphere                       [same units as lambda0]
  * `λ0`: wavelength in a vacuum                          [same units as d]
  * `µ`: the cos(θ) of each direction desired             [-]
  * `n_env`: real index of medium around sphere, optional.

# Output

`ipar`, `iper`: scattered intensity in parallel and perpendicular planes [1/sr]
