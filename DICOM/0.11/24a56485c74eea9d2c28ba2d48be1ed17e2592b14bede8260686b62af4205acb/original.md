```
lookup_vr(tag::Tuple{Integer,Integer})
```

Return VR value for tag from DICOM dictionary

# Example

```jldoctest
julia> lookup_vr((0x0028,0x0004))
"CS"
```
