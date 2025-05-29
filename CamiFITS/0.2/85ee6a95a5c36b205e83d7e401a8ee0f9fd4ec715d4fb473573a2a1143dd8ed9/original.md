```
fits_collect(fileStart::String, fileStop::String [; protect=true [, msg=true]])
```

Combine "fileStart" with "fileStop" (with mandatory ".fits" extension)

Key:

  * `protect::Bool`: overwrite protection
  * `msg::Bool`: allow status message

#### Example:

```
julia> for i=1:5
           data = [0 0 0; 0 i 0; 0 0 0]
           fits_create("T$i.fits", data; protect=false)
       end

julia> f = fits_collect("T1.fits", "T5.fits"; protect=false);
'T1-T5.fits': file created

julia> fits_info(f)[:,:,2]

File: T1-T5.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Int64
Datasize: (3, 3, 5)

Metainformation:
SIMPLE  =                    T / file does conform to FITS standard
BITPIX  =                   64 / number of bits per data pixel
NAXIS   =                    3 / number of data axes
NAXIS1  =                    3 / length of data axis 1
NAXIS2  =                    3 / length of data axis 2
NAXIS3  =                    5 / length of data axis 3
EXTEND  =                    T / FITS dataset may contain extensions
END

3×3 Matrix{Int64}:
 0  0  0
 0  2  0
 0  0  0

julia> for i = 1:5 rm("T$i.fits") end

julia> rm("T1-T5.fits"); f = nothing
```
