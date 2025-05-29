```
pix2ringpos(resol::Resolution, pixel)
```

Given the (1-based) index of a pixel in a Healpix map in ring order, return a pair of numbers (n, i, j) whose meaning is the following:

  * `n` can be one of the symbols `:northcap`, `:equator`, or `:southcap`, representing the region of the sky
  * `i` is the ring index, from 1 to 4NSIDE - 1
  * `j` is the pixel-in-ring index
