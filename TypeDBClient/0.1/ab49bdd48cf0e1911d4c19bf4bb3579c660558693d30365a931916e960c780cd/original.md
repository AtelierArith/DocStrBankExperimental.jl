```
set_supertype(r::RemoteConcept{<: AbstractThingType,<: AbstractCoreTransaction},
    super_type::AbstractThingType)
```

Here we have the chance to set a given ThingType as the supertype of an other Thingtype. Mixing of diffent root types eg. AttributeType with EntityType is not allowed.
