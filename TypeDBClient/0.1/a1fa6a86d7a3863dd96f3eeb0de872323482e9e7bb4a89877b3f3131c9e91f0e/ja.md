```
get_owns(
    r::RemoteConcept{<:AbstractThingType},
    value_type::Optional{EnumType}=nothing,
    keys_only::Bool=false
)
```

get_ownsは、指定されたAttributeTypeを所有するすべてのthingtypeを返します。
