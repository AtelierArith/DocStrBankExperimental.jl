```
cast_FITS_filnam(filnam::String)
```

[`FITS_filnam`](@ref) オブジェクトを作成して、`filnam` を `name`、`prefix`、`numerator`、および `extension` に分解します。

#### 例:

```
julia> filnam = "T23.01.fits";

julia> n = cast_FITS_filnam(filnam);

julia> n.name, n.prefix, n.numerator, n.extension
("T23.01", "T23.", "01", ".fits")
```
