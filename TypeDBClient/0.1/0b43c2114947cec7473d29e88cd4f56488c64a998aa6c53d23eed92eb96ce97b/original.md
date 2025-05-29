```
delete(r::RemoteConcept{<:AbstractThingType})
```

To delete a type in the database pack the type with the transaction to a RemoteConcept. Be aware that a type can only be deleted if no Entity, Attribute or Relation is in the database which is based on this type.
