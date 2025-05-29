```
FITS_dataobject
```

指定された `hdutype` の [`FITS_HDU`](@ref) のデータを保持するオブジェクトです。

フィールドは次のとおりです：

  * `.hdutype`:  受け入れられるタイプは 'PRIMARY'、'IMAGE'、および 'TABLE' (`::String`)
  * `.data`:  `hdutype` に適した形式で (::Any)
