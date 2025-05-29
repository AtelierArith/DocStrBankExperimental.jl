```
SuptBand(nuncovered::Real=0; ndraw::Real=1_000_000)
```

Return a `SuptBand` instance that requires `ndraw` random numbers for computation. Results tend to be more accurate with a larger value of `ndraw`.

A positive value of `nuncovered` allows generalized error rate control described by Montiel Olea and Plagborg-Møller (2019). Specifically, at most `nuncovered` number of point estimates are allowed to be not covered by the confidence band when considering the coverage.

# References

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
