```
@tag_str(s)
```

文字列 `s` に対応する DICOM タグを返します。

```jldoctest
julia> using DICOM

julia> tag"ROI Mean"
(0x6000, 0x1302)
```
