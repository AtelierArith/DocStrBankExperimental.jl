```
pix2angRing(resol::Resolution, pixel) -> (Float64, Float64)
```

Given the (1-based) index of a pixel in a Healpix map in ring order, return a pair containing the (`colatitude`, `longitude`) angles corresponding to its center, both expressed in radians.
