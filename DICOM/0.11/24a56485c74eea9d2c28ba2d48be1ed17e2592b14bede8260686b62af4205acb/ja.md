```
lookup_vr(tag::Tuple{Integer,Integer})
```

DICOM 辞書からタグの VR 値を返します

# 例

```jldoctest
julia> lookup_vr((0x0028,0x0004))
"CS"
```
