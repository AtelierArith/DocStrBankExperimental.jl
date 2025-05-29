```
HemisphericParcellation{T}(surface, x)
```

Create a `HemisphericParcellation` from a `Vector` `x`, the length of which should match  the size of the `surface::Hemisphere` being supplied. The distinct elements of that `Vector` will become the `Parcels` of the resulting struct. Parcels will be keyed by IDs of type `T`; therefore the eltype of the `Vector` you supply must be coercable to `T`.
