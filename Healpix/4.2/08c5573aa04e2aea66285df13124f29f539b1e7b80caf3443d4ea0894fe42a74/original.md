```
order2nside(order::Integer)
```

Return the value of NSIDE for a given order. If the given order is not valid, throw a `DomainError` exception.

If you have created a [`Healpix.Resolution`](@ref) object, you can access the value of NSIDE through the field `nside`.

See also [`nside2order`](@ref).
