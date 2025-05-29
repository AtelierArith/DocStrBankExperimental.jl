```
i_per(m, x, μ; norm = :albedo)
```

Return the scattered intensity in a plane normal to the incident light. This is the scattered intensity in a plane that is perpendicular to the field of the incident plane wave. The intensity is normalized such that the integral of the unpolarized intensity over 4π steradians is equal to the single scattering albedo.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `µ`: the angles, cos(theta), to calculate intensities

# Output

The intensity at each angle in the array µ.  Units [1/sr]
