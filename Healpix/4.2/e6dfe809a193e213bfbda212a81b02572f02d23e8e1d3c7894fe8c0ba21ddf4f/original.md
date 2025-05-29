```
numberOfAlms(lmax::Integer, mmax::Integer) -> Integer
numberOfAlms(lmax::Integer) -> Integer
```

Return the size of the array of complex numbers needed to store the a_ℓm coefficients in the range of ℓ and m specified by `lmax` and `mmax`. If `mmax` is not specified, it is assumed to be equal to `lmax`. If `lmax` and `mmax` are inconsistent or negative, a `DomainError` exception is thrown.
