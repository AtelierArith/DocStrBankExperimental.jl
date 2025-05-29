```
mie_cdf(m, x, num; norm = :albedo)
```

Create a CDF for unpolarized scattering for uniform CDF. The CDF covers scattered (exit) angles ranging from 180 to 0 degrees. (The cosines are uniformly distributed over -1 to 1.) These angles mu correspond to uniform spacing of the cumulative distribution function for unpolarized Mie scattering where cdf[i] = i/(num-1). This is a brute force implementation that solves the problem by calculating the CDF at many points and then scanning to find the specific angles that correspond to uniform interval of the CDF. Since this is a cumulative distribution function, the maximum value should be 1.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `num`: length of desired CDF array

# Output

  * `µ`: array of cosines of angles (irregularly spaced)
  * `cdf`: array of cumulative distribution function values
