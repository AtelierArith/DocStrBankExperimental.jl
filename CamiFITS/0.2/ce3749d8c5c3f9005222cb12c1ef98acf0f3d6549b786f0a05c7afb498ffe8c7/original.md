```
fits_edit_key!(f::FITS, hduindex::Int, key::String, val::Any, com::String)
```

Edit a header record of given 'key, value and comment' to 'HDU[hduindex]' of file with name 'filnam'

#### Example:

```
julia> filnam="foo.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_add_key!(f, 1, "KEYNEW1", true, "this is the inserted record");

julia> i = get(f.hdu[1].header.map, "KEYNEW1", 0)
6

julia> fits_edit_key!(f, 1, "KEYNEW1", data, "record $i changed to a DateTime type");

julia> fits_info(f.hdu[1]; nr=true);
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

  nr | Metainformation:
---------------------------------------------------------------------------------------
   1 | SIMPLE  =                    T / file does conform to FITS standard
   2 | BITPIX  =                   64 / number of bits per data pixel
   3 | NAXIS   =                    1 / number of data axes
   4 | NAXIS1  =                    0 / length of data axis 1
   5 | EXTEND  =                    T / FITS dataset may contain extensions
   6 | KEYNEW1 = '2020-01-01T00:00:0' / record 6 changed to a DateTime type
   7 | END
```
