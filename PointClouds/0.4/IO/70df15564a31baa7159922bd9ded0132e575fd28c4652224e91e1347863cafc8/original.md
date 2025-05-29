```
extra_bytes(p::PointRecord)
extra_bytes(points, inds = :)
```

Obtain the “extra bytes” of a point record as a tuple of `UInt8`s. The meaning of these bytes may be described with a variable-length record.

See also: [`PointRecord`](@ref), [`user_data`](@ref)
