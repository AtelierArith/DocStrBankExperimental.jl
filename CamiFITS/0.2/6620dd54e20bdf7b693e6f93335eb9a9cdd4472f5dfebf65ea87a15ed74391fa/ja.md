```
FITS(filnam::String, hdu::Vector{FITS_HDU})
```

単一の `.fits` ファイルを保持するオブジェクトです。

フィールドは次のとおりです。

  * `.filnam`: 対応する `.fits` ファイルのファイル名 (`::String`)
  * `.hdu`: [`FITS_HDU`](@ref) の配列 (`::Vector{FITS_HDU}`)

#### 例:

```
julia> data = [11 21 31; 12 22 23; 13 23 33];

julia> d = cast_FITS_dataobject("image", data);

julia> h = cast_FITS_header(d);

julia> hdu = cast_FITS_HDU(1, h, d);

julia> f = cast_FITS("test.fits", [hdu]);

julia> f.hdu[1].dataobject.data
3×3 Matrix{Int64}:
 11  21  31
 12  22  23
 13  23  33
```
