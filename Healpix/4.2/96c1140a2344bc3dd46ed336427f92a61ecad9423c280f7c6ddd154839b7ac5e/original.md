```
queryDiscRing(resol::Resolution, theta, phi, radius; fact=0)
```

Return a list of the indices of those pixels whose centers are closer than `radius` to direction `(theta, phi)`. The three angles `radius`, `theta`, and `phi` must be expressed in radians.

If `fact` is nonzero, it must be a positive integer; it requires to carry the computation at a resolution `fact * nside`.
