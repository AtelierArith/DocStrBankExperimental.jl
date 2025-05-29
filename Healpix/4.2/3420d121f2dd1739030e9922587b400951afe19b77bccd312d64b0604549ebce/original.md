```
ang2pix{T, O, AA}(map::HealpixMap{T, O}, theta, phi)
ang2pix{T, O, AA}(map::PolarizedHealpixMap{T, O}, theta, phi)
```

Convert the direction specified by the colatitude `theta` (∈ [0, π]) and the longitude `phi` (∈ [0, 2π]) into the index of the pixel in the Healpix map `map`.
