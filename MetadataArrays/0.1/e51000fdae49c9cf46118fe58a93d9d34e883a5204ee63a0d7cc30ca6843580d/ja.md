```
MetadataArray(parent::AbstractArray, metadata)
```

カスタム `AbstractArray` オブジェクトで、`AbstractArray` `parent` といくつかの `metadata` を格納します。

# 例

```jldoctest metadataarray
julia> v = ["John", "John", "Jane", "Louise"];

julia> s = MetadataArray(v, Dict("John" => "Treatment", "Louise" => "Placebo", "Jane" => "Placebo"))
4-element MetadataArrays.MetadataArray{String,Dict{String,String},1,Array{String,1}}:
 "John"
 "John"
 "Jane"
 "Louise"

julia> metadata(s)
Dict{String,String} with 3 entries:
  "John"   => "Treatment"
  "Jane"   => "Placebo"
  "Louise" => "Placebo"
```
