```
fits_read(filnam::String)
```

Read `.fits` file and return Array of `FITS_HDU`s

![Image](../assets/fits_read.png)

#### Example:

```
julia> filnam = "minimal.fits";

julia> fits_create(filnam; protect=false);

julia> f = fits_read(filnam);

julia> fits_info(f)
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
END

Any[]

julia> rm(filnam); f = nothing
```
