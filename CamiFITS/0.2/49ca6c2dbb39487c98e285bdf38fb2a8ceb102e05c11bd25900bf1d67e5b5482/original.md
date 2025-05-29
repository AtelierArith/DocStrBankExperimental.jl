```
cast_FITS_ptr(o::IO [; msg=false])
cast_FITS_ptr(p::FITS_pointer)
```

Prefered method to construct a [`FITS_ptr`](@ref) object.

#### Example:

```
julia> filnam = "foo.fits";
julia> data = [0x0000043e, 0x0000040c, 0x0000041f];
julia> f = fits_create(filnam, data; protect=false);
julia> fits_extend(f, data; hdutype="'IMAGE   '");
julia> fits_extend(f, data; hdutype="'IMAGE   '");
julia> o = IORead(filnam);

julia> ptr = cast_FITS_ptr(o; msg=true)
             block count: 6
               hdu count: 3
 start-of-block pointers: [0, 2880, 5760, 8640, 11520, 14400]
   end-of-block pointers: [2880, 5760, 8640, 11520, 14400, 17280]
   start-of-hdu pointers: [0, 5760, 11520]
     end-of-hdu pointers: [5760, 11520, 17280]
start-of-header pointers: [0, 5760, 11520]
  end-of-header pointers: [2880, 8640, 14400]
  start-of-data pointers: [2880, 8640, 14400]
    end-of-data pointers: [8640, 14400, 17280]

FITS_ptr(HDU_ptr[HDU_ptr(Ptrs(0, 2880), Ptrs(2880, 8640)), HDU_ptr(Ptrs(5760, 8640), Ptrs(8640, 14400)), HDU_ptr(Ptrs(11520, 14400), Ptrs(14400, 17280))])

julia> p.hdu[2].header.start, p.hdu[2].data.start
(5760, 8640)
```
