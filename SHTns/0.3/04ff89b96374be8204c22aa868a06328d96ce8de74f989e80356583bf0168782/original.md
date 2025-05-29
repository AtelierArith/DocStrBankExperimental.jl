```
analys!(cfg::SHTnsCfg, v, qlm)
analys!(cfg::SHTnsCfg, utheta, uphi, slm, tlm)
analys!(cfg::SHTnsCfg, ur, utheta, uphi, qlm, slm, tlm)
```

In-place transforms of the spatial data into spherical harmonics coefficients for scalar, 2D or 3D fields.

!!! warning
    This function modifies the input arrays `v`, `ur`, `utheta` and `uphi`.

