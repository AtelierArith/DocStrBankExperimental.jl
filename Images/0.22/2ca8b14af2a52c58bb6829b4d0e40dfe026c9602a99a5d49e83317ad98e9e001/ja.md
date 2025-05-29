`imadjustintensity(img [, (minval,maxval)]) -> Image`

強度を区間 `(minval,maxval)` から区間 `[0,1]` にマッピングします。これは `map(ScaleMinMax(eltype(img), minval, maxval), img)` と同等です。(minval,maxval) のデフォルトは `extrema(img)` です。
