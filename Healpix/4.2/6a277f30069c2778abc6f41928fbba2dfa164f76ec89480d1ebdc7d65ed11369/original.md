```
nside2npix(nside::Integer) -> Integer
```

Return the number of pixels for a Healpix map with the specified `NSIDE` value. If `NSIDE` is not an integer power of two, the function throws a `DomainError` exception.
