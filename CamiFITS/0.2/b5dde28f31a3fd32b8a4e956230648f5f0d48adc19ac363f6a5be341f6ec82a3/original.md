```
fits_save_as(f::FITS, filnam::String [; protect=true])
```

Save the [`FITS`](@ref) object under the name `filnam`. Key:

  * `protect::Bool`: overwrite protection

```
julia> f = fits_create("minimal.fits"; protect=false);

julia> fits_save_as(f, "foo.fits"; protect=false);

julia> f = fits_read("foo.fits");

julia> fits_info(f)
File: foo.fits
hdu: 1
hdutype: PRIMARY
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
END

Any[]
```
