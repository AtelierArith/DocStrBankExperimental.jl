```
@tag_str(s)
```

Return the dicom tag, corresponding to the string `s`.

```jldoctest
julia> using DICOM

julia> tag"ROI Mean"
(0x6000, 0x1302)
```
