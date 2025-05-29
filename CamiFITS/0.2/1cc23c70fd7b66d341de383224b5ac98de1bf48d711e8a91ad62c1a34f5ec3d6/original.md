```
fits_rename_key!(filnam::String, hduindex::Int, keyold::String, keynew::String)
```

Rename the key of a header record of file with name 'filnam'

#### Example:

```
julia> filnam="minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_add_key!(f, 1, "KEYNEW1", true, "this is a new record");

julia> fits_rename_key!(f, 1, "KEYNEW1",  "KEYNEW2");

julia> fits_info(f.hdu[1])
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

Metainformation:
SIMPLE  =                    T / file does conform to FITS standard
BITPIX  =                   64 / number of bits per data pixel
NAXIS   =                    1 / number of data axes
NAXIS1  =                    0 / length of data axis 1
BZERO   =                  0.0 / offset data range to that of unsigned integer
BSCALE  =                  1.0 / default scaling factor
EXTEND  =                    T / FITS dataset may contain extensions
COMMENT    Extended FITS HDU   / http://fits.gsfc.nasa.gov/
KEYNEW2 =                    T / this is a new record
END

Any[]
```
