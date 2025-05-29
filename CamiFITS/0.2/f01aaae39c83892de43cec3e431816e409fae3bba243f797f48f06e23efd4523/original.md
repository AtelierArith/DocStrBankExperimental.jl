```
cast_FITS_HDU(hduindex::Int, header::FITS_header, data::FITS_dataobject)
```

Create the [`FITS_HDU`](@ref) object for given `hduindex`, `header` and `data`.

#### Example:

```
julia> data = [11 21 31; 12 22 23; 13 23 33];

julia> d = cast_FITS_dataobject("image", data);

julia> h = cast_FITS_header(d);

julia> hdu = cast_FITS_HDU(1, h, d);

julia> hdu.dataobject.data
3×3 Matrix{Int64}:
 11  21  31
 12  22  23
 13  23  33
```
