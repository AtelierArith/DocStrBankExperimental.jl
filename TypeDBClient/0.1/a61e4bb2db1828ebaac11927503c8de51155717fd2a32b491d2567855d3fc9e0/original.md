```
set_plays(
    r::RemoteConcept{<:AbstractThingType},
    role_type::AbstractRoleType,
    overridden_role_type::Optional{AbstractRoleType}=nothing
)
```

With set_play we are able to set a roletype to an ThingType and it is possible to set a new RoleType instead of the old. Be cautious, this is only allowed for not instantiated types.
