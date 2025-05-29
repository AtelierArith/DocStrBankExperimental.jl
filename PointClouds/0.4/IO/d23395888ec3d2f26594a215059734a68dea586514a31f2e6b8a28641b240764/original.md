```
user_data([T], p::PointRecord)
user_data([T], points, inds = :)
```

Obtain the “user data” of a point record, which is defined as an integer between 0 and 255. This data is included in all PDRFs but does not have any standardized meaning.

See also: [`PointRecord`](@ref), [`extra_bytes`](@ref)
