```
fits_info(f::FITS [, hduindex=1 [; nr=false [, hdr=true]]])
fits_info(hdu::FITS_HDU; nr=false, hdr=true)
```

Metafinformation and data of a given [`FITS_HDU`](@ref) object with *optional* record numbering. 

  * `hduindex`: HDU index (::Int - default: `1` = `primary hdu`)
  * `nr`: include cardindex (::Bool - default: `false`)
  * `hdr`: show header (::Bool)

#### Example:

To demonstrate `fits_info` we first create the fits object `f` for subsequent  inspection.

```
julia> filnam = "minimal.fits";

julia> f = fits_create(filnam; protect=false);

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
END

Any[]

julia> rm(filnam); f = nothing
```

```
fits_info(filnam::String [, hduindex=1 [; nr=true [, hdr=true]]])
```

Same as above but creating the fits object by reading `filnam` from disc  and with *default* record numbering.

  * `hduindex`: HDU index (::Int - default: `1` = `primary hdu`)
  * `nr`: include cardindex (::Bool - default: `true`)
  * `hdr`: show header (::Bool)

#### Example:

```
julia> filnam = "minimal.fits";

julia> fits_create(filnam; protect=false);

julia> fits_info(filnam)

File: minimal.fits
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
   6 | END

Any[]

julia> rm(filnam)
```
