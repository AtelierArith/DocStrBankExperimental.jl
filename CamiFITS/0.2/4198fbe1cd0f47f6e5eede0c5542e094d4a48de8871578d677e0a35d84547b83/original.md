```
cast_FITS_filnam(filnam::String)
```

Create the [`FITS_filnam`](@ref) object to decompose `filnam` into its `name`,  `prefix`, `numerator` and `extension`.

#### Example:

```
julia> filnam = "T23.01.fits";

julia> n = cast_FITS_filnam(filnam);

julia> n.name, n.prefix, n.numerator, n.extension
("T23.01", "T23.", "01", ".fits")
```
