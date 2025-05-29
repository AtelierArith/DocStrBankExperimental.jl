```
cast_FITS_dataobject(hdutype::String, data)
```

指定された `hdutype` に従って `data` から構築された `hduindex` のための [`FITS_dataobject`](@ref) オブジェクトを作成します: *PRIMARY*, *IMAGE*, *ARRAY*, *TABLE* (ASCII テーブル) または *BINTABLE* (バイナリテーブル)。

#### 例:

```
julia> data = [11,21,31,12,22,23,13,23,33];

julia> data = reshape(data,(3,3));

julia> d = cast_FITS_dataobject("image", data)
FITS_dataobject("'IMAGE   '", [11 12 13; 21 22 23; 31 23 33])

julia> d.data
3×3 Matrix{Int64}:
 11  12  13
 21  22  23
 31  23  33

julia> d.hdutype
"'IMAGE   '"
```
