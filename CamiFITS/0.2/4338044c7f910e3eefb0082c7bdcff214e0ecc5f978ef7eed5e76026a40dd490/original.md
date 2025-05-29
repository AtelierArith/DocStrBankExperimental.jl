```
fits_extend(f::FITS, data [; hdutype="IMAGE"])
fits_extend(filnam::String, data [; hdutype="IMAGE"])
```

[`FITS`](@ref) object `f` extended by a [`FITS_HDU`](@ref) object constructed from the `data` in the format of the `hdutype` keyword. 

Shorthand function: For a file on disc under the name `filnam`

```
julia> f = fits_extend(filnam, data; hdutype="foo")
```

is equivalent to

```
julia> f = fits_read(filnam);

julia> fits_extend(f, data; hdutype="foo")
```

NB. For the details of the save procedure (not shown in the flow diagram) 

  * see [`fits_save`](@ref).

![Image](../assets/fits_extend.png)

#### Examples:

```
julia> filnam = "foo.fits";

julia> fits_create(filnam; protect=false);

julia> table = let
        [true, 0x6c, 1081, 0x0439, 1.23, 1.01f-6, 1.01e-6, 'a', "a", "abc"],
        [false, 0x6d, 1011, 0x03f3, 23.2, 3.01f-6, 3.01e-6, 'b', "b", "abcdef"]
        end;

julia> fits_extend(filnam, table; hdutype="table");

julia> fits_info(filnam, 2; hdr=false)
2-element Vector{String}:
 " 1 108 1081 1081  1.23 1.01E-6 1.01D-6 a a    abc"
 " 0 109 1011 1011 23.20 3.01E-6 3.01D-6 b b abcdef"

julia> rm(filnam)
```
