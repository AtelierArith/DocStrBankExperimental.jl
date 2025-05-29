```
fits_create(filnam [, data [; protect=true]])
```

Create and [`fits_save`](@ref) a `.fits` file of given `filnam` and return the  [`FITS`](@ref) object in the form of an Array of [`FITS_HDU`](@ref)s.

Key:

  * `data`: data primary hdu (::DataType)
  * `protect`: overwrite protection (::Bool)

NB. For the details of the save procedure (not shown in the flow diagram) -  see [`fits_save`](@ref).

![Image](../assets/fits_create.png)

#### Examples:

```
julia> filnam = "foo.fits";

julia> data = [11,21,31,12,22,23,13,23,33];

julia> data = reshape(data,(3,3,1));

julia> f = fits_create(filnam, data; protect=false);

julia> fits_info(f)

File: foo.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Int64
Datasize: (3, 3, 1)

Metainformation:
SIMPLE  =                    T / file does conform to FITS standard
BITPIX  =                   64 / number of bits per data pixel
NAXIS   =                    3 / number of data axes
NAXIS1  =                    3 / length of data axis 1
NAXIS2  =                    3 / length of data axis 2
NAXIS3  =                    1 / length of data axis 3
EXTEND  =                    T / FITS dataset may contain extensions
END

3×3×1 Array{Int64, 3}:
[:, :, 1] =
 11  12  13
 21  22  23
 31  23  33

julia> rm(filnam); f = nothing
```
