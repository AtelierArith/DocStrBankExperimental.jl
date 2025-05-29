```
fits_delete_key!(f::FITS, hduindex::Int, key::String)
```

Delete a [`FITS_card`](@ref) record of given `key`, `value` and `comment` from the  [`FITS_HDU`](@ref) `f.hdu[hduindex]`.

#### Examples:

```
julia> filnam = "foo.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_add_key!(f, 1, "KEYNEW1", true, "This is the new key");

julia> cardindex = get(f.hdu[1].header.map,"KEYNEW1", nothing)
8

julia> keyword = f.hdu[1].header.card[cardindex].keyword
"KEYNEW1"

julia> cardindex = get(f.hdu[1].header.map,"KEYNEW1", nothing)
8

julia> fits_delete_key!(f, 1, "KEYNEW1");

julia> cardindex = get(f.hdu[1].header.map,"KEYNEW1", nothing)

julia> fits_delete_key!(f, 1, "NAXIS");
ERROR: FITSError: 17 - illegal keyword deletion (mandatory keyword)
Stacktrace:
 [1] fits_delete_key!(f::FITS, hduindex::Int64, key::String)
   @ CamiFITS c:\Users\walra\.julia\dev\CamiFITS.jl\src\fits_public_sector.jl:495
 [2] top-level scope
   @ REPL[24]:1
```
