```
set_owns(
    r::RemoteConcept{<:AbstractType},
    attribute_type::AbstractType,
    is_key::Bool=false,
    overriden_type::Optional{AbstractType}=nothing
)
```

With set_owns it is possible to assign an attribute to a type. If it is needed it is possible to set the attribute as unique. This means for the type where the attribute is set as key only one instance of the type can have a specific attribute: E.g. person entity has a unique email as an attribute. So it is not possible to have two entities with the same email address.
