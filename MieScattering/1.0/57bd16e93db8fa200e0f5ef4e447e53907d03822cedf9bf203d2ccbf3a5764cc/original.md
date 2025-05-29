```
i_unpolarized(m, x, μ; norm = :albedo)
```

Return the unpolarized scattered intensity at specified angles. This is the average value for randomly polarized incident light. The intensity is normalized such that the integral of the unpolarized intensity over 4π steradians is equal to the single scattering albedo.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `µ`: the angles, cos(theta), to calculate intensities

# Output

The intensity at each angle in the array µ.  Units [1/sr]
