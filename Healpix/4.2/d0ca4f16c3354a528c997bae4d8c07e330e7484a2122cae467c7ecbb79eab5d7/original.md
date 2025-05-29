```
npix2nside(npix::Integer) -> Integer
```

Given the number of pixels in a Healpix map, return the `NSIDE` resolution parameter. If the number is invalid, throw a `DomainError` exception.
