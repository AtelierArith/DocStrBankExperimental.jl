```
mie_cdf(m, x, num; norm = :albedo)
```

Create a CDF for unpolarized scattering uniformly spaced in cos(θ). The CDF covers scattered (exit) angles ranging from 180 to 0 degrees. (The cosines are uniformly distributed over -1 to 1.) Because the angles are uniformly distributed in cos(theta), the scattering function is not sampled uniformly and therefore huge array sizes are needed to adequately sample highly anisotropic phase functions. Since this is a cumulative distribution function, the maximum value should be 1.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `num`: length of desired CDF array

# Output

  * `µ`: array of cosines of angles
  * `cdf`: array of cumulative distribution function values
