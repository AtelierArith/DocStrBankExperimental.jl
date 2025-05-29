```
struct Resolution
```

`Resolution` objects are needed to perform a number of pixel-related functions, e.g., convert a direction into a pixel number and vice versa.

The fields of a `Resolution` object are the following:

  * `nside`: the NSIDE parameter
  * `nsideTimesTwo`: 2 * NSIDE
  * `nsideTimesFour`: 4 * NSIDE
  * `numOfPixels`: number of pixels in the map
  * `order`: order of the map
  * `pixelsPerFace`: number of pixels in each Healpix face
  * `ncap`
  * `fact2`
  * `fact1`
