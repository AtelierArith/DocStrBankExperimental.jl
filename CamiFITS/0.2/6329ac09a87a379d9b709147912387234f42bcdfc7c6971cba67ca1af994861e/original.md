```
fits_copy(filnam1 [, filnam2="" [; protect=true]])
```

Copy `filnam1` to `filnam2` (with mandatory `.fits` extension) Key:

  * `protect::Bool`: overwrite protection
  * `msg::Bool`: allow status message

#### Examples:

```
julia> filnam = "foo.fits";

julia> fits_create("foo1.fits"; protect=false);

julia> fits_copy("foo1.fits", "foo2.fits"; protect=false);
'foo1.fits' was copied to 'foo2.fits'

julia> rm.(["foo1.fits", "foo2.fits"]);
```
