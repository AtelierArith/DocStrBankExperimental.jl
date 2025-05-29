```
cast_FITS_dataobject(hdutype::String, data)
```

Create the [`FITS_dataobject`](@ref) object for given `hduindex` constructed from  the `data` in accordance to the specified `hdutype`: *PRIMARY*,  *IMAGE*, *ARRAY*, *TABLE* (ASCII table) or *BINTABLE* (binary table).

#### Example:

```
julia> data = [11,21,31,12,22,23,13,23,33];

julia> data = reshape(data,(3,3));

julia> d = cast_FITS_dataobject("image", data)
FITS_dataobject("'IMAGE   '", [11 12 13; 21 22 23; 31 23 33])

julia> d.data
3×3 Matrix{Int64}:
 11  12  13
 21  22  23
 31  23  33

julia> d.hdutype
"'IMAGE   '"
```
