```
fits_pointer(filnam::String)
fits_pointer(f::FITS)
```

[`FITS_pointer`](@ref) オブジェクトのファイル `filnam` またはその [`FITS`](@ref) オブジェクト `f`。

#### 例:

```
julia> filnam = "foo.fits";

julia> f = fits_create(filnam, data; protect=false);

julia> fits_extend(f; hdutype="'IMAGE   '");

julia> fits_extend(filnam, data; hdutype="'IMAGE   '");

julia> p = fits_pointer(f);

julia> p.nblock
5
```
