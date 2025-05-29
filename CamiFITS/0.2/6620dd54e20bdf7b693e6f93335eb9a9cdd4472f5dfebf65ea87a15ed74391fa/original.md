```
FITS(filnam::String, hdu::Vector{FITS_HDU})
```

Object to hold a single `.fits` file.

The fields are

  * `.filnam`:  filename of the corresponding `.fits` file (`::String`)
  * `.hdu`:  array of [`FITS_HDU`](@ref)s (`::Vector{FITS_HDU}`)

#### Example:

```
julia> data = [11 21 31; 12 22 23; 13 23 33];

julia> d = cast_FITS_dataobject("image", data);

julia> h = cast_FITS_header(d);

julia> hdu = cast_FITS_HDU(1, h, d);

julia> f = cast_FITS("test.fits", [hdu]);

julia> f.hdu[1].dataobject.data
3×3 Matrix{Int64}:
 11  21  31
 12  22  23
 13  23  33
```
