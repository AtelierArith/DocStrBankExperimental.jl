```
get_has(transaction::AbstractCoreTransaction,
    thing::AbstractThing,
    attribute_type::Optional{AttributeType} = nothing,
    attribute_types::Optional{Vector{<:AbstractAttributeType}} = nothing,
    keys_only = false)
```

With this function it is possible to get attributes of an entity or a relation. Optional it is possible to restrict the type(s) of attributes which will retrieved from the database. You can decide between only one ore more than one type.
