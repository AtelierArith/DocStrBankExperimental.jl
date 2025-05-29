```
fits_pointers(filnam::String)
fits_pointers(f::FITS)
```

summary of the pointers internally used by *CamiFITS*

#### Examples:

```
julia> filnam = "foo.fits";

julia> data = [0x0000043e, 0x0000040c, 0x0000041f];

julia> f = fits_create(filnam, data; protect=false);

julia> fits_extend(f);

julia> fits_extend(filnam, data; hdutype="'IMAGE   '");

julia> foreach(println, fits_pointers(filnam))
             block count: 5
               hdu count: 3
 start-of-block pointers: (0, 2880, 5760, 8640, 11520)
   end-of-block pointers: (2880, 5760, 8640, 11520, 14400)
   start-of-hdu pointers: (0, 5760, 8640)
     end-of-hdu pointers: (2880, 8640, 11520)
start-of-header pointers: (0, 5760, 8640)
  end-of-header pointers: (2880, 8640, 11520)
  start-of-data pointers: (2880, 8640, 11520)
    end-of-data pointers: (5760, 8640, 14400)
```
