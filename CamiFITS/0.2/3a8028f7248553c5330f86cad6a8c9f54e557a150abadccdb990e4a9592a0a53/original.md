```
cast_FITS_pointer(o::IO)
```

Prefered method to construct a [`FITS_pointer`](@ref) object.

#### Example:

```
julia> filnam = "foo.fits";

julia> data = [0x0000043e, 0x0000040c, 0x0000041f];

julia> f = fits_create(filnam, data; protect=false);

julia> fits_extend(f, data; hdutype="'IMAGE   '");

julia> fits_extend(f, data; hdutype="'IMAGE   '");

julia> o = IORead(filnam);

julia> p = cast_FITS_pointer(o);

 julia> p.nblock, p.nhdu, p.block_start, p.block_stop, p.hdu_start, p.hdr_stop
 (6, 3, (0, 2880, 5760, 8640, 11520, 14400), (2880, 5760, 8640, 11520, 14400, 17280), (0, 5760, 11520), (2880, 8640, 14400))
    
 julia> p.hdr_start, p.hdr_stop, p.data_start, p.data_stop
 ((0, 5760, 11520), (2880, 8640, 14400), (2880, 8640, 14400), (8640, 14400, 17280))
```
