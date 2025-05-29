```
fits_record_dump(filnam [, hduindex=0 [; hdr=true [, dat=true [, nr=true [, msg=true]]]])
```

The file `filnam` as a `Vector{String}` of 80 character strings (records)  without any further formatting. 

For `msg=true``it outputs a listing of`filnam` in blocks (2880 bytes) of 36  (optionally indexed) records. The dump proceeds *without casting of FITS objects*;  i.e., *without* FITS-conformance testing.

default: `hduindex` = 0 - all blocks          `hduindex` > 0 - only blocks of given `hduindex`

  * `hduindex`: HDU index (::Int - default: `0` all records)
  * `hdr`: show header (::Bool - default: true)
  * `dat`: show data (::Bool - default: true)
  * `nr`: include record index (row number) (::Bool - default: true)
  * `msg`: print message (::Bool)

NB. The tool `fits_record_dump` is included for developers to facilitate code analysis  of the *CamiFITS* package (e.g. the correct implementation of `ENDIAN` wraps  and the zero-offset shifting). 

#### Example:

```
julia> filnam = "foo.fits";

julia> data = [typemin(UInt32),typemax(UInt32)];

julia> fits_create(filnam, data; protect=false);

julia> dump = fits_record_dump(filnam; msg=false);

julia> foreach(println,dump[3:8])
   3 | NAXIS   =                    1 / number of data axes
   4 | NAXIS1  =                    2 / length of data axis 1
   5 | BSCALE  =                  1.0 / default scaling factor
   6 | BZERO   =           2147483648 / offset data range to that of unsigned integer
   7 | EXTEND  =                    T / FITS dataset may contain extensions
   8 | END

julia> dump[37]
"  37 | UInt8[0x80, 0x00, 0x00, 0x00, 0x7f, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, ⋯, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]"]"

julia> rm(filnam); f = data = dump = nothing
```
