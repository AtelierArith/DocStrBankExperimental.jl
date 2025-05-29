```
fits_insert_key!(f::FITS, hduindex::Int, cardindex::Int, key::String, val::Any, com::String)
```

Insert one or more [`FITS_card`]s for given 'key', 'value' and 'comment' at position `cardindex`  in `f.hdu[hduindex].header.card`; i.e., into the record stack of the [`FITS_header`](@ref) of the  [`FITS_HDU`](@ref)`[hduindex]` of the [`FITS`](@ref) object 'f'.

NB. For insert without specification of `cardindex`use [`fits_add_key!`](@ref).

#### Example:

```
julia> filnam = "minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_insert_key!(f, 1, 3, "KeYNEw1", true, "This is the new key");

julia> fits_info(f;nr=true);

File: minimal.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

  nr | Metainformation:
---------------------------------------------------------------------------------------
   1 | SIMPLE  =                    T / file does conform to FITS standard
   2 | BITPIX  =                   64 / number of bits per data pixel
   3 | KEYNEW8 =                    T / This is the new key
   4 | NAXIS   =                    1 / number of data axes
   5 | NAXIS1  =                    0 / length of data axis 1
   6 | EXTEND  =                    T / FITS dataset may contain extensions
   7 | END
```
