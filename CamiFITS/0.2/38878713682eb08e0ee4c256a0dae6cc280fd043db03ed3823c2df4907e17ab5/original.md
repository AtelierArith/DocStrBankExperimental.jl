```
fits_pointer(filnam::String)
fits_pointer(f::FITS)
```

[`FITS_pointer`](@ref) object of the file `filnam` or its [`FITS`](@ref) object `f`.

#### Examples:

```
julia> filnam = "foo.fits";

julia> f = fits_create(filnam, data; protect=false);

julia> fits_extend(f; hdutype="'IMAGE   '");

julia> fits_extend(filnam, data; hdutype="'IMAGE   '");

julia> p = fits_pointer(f);

julia> p.nblock
5
```
