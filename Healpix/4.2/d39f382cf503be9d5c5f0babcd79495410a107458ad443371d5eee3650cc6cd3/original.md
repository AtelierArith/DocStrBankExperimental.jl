```
nside2order(nside::Integer)
```

Return the order (positive integer) associated with a given NSIDE. If the given nside is not valid, throw a `DomainError` exception.

If you have created a [`Healpix.Resolution`](@ref) object, you can access the order through the field `order`.

See also [`order2nside`](@ref).
