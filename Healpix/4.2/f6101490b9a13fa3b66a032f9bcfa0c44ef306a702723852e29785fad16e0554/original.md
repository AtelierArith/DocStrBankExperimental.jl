```
zphi2pixRing(resol::Resolution, theta, phi) -> Integer
```

Return the index of the pixel which contains the point with coordinates (`theta`, the colatitude, and `phi`, the longitude), in radians, for a Healpix map with pixels in ring order. Note that pixel indexes are 1-based (this is Julia)!
