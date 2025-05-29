```
ldos(gf::GreenFunction, E[, site; broaden])
ldos(gf::GreenFunction, site[; broaden])
```

Calculates the LDOS (local density of states) for a given Green's function at energy `E`. `broaden` is the broadening factor for the energy levels, default is `0.1`.

If `site` is not specified, the LDOS for all sites is calculated and returned as a `LatticeValue`. Otherwise, the LDOS for the given site is returned as a `Real` value.

If `E` is not specified, a function that calculates the LDOS at site `site` for given energy is returned.
