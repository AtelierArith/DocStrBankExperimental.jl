```
convertlookup(dstlookup::Type{<:Lookup}, x)
```

Convert the dimension lookup between `Projected` and `Mapped`. Other dimension lookups pass through unchanged.

This is used to e.g. save a netcdf file to GeoTiff.
