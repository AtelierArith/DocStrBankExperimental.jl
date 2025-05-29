```
fits_add_key!(f::FITS, hduindex::Int, key::String, val::Any, com::String)
```

Insert one or more [`FITS_card`]s for given 'key', 'value' and 'comment' at  *non-specified* position in `f.hdu[hduindex].header.card`; i.e., into the record  stack of the [`FITS_header`](@ref) of the [`FITS_HDU`](@ref)`[hduindex]` of the  [`FITS`](@ref) object 'f'.      

#### Example:

```
julia> filnam = "minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_add_key!(f, 1, "KEYNEW1", true, "This is the new key");

julia> fits_info(f)

File: minimal.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

Metainformation:
SIMPLE  =                    T / file does conform to FITS standard
BITPIX  =                   64 / number of bits per data pixel
NAXIS   =                    1 / number of data axes
NAXIS1  =                    0 / length of data axis 1
EXTEND  =                    T / FITS dataset may contain extensions
KEYNEW1 =                    T / This is the new key
END

Any[]
```
