```
equal_solid_angles (ntheta, nphi)
```

Discretize the sky into `ntheta` zenith rings and a number of sectors per ring that is proportional to `sin(θ)`. The total number of sectors will be `ntheta*nphi`. Returns an object of type `SkySectors`. See package documentation for details.
