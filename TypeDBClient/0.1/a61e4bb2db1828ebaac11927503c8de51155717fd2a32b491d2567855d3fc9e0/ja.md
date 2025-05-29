```
set_plays(
    r::RemoteConcept{<:AbstractThingType},
    role_type::AbstractRoleType,
    overridden_role_type::Optional{AbstractRoleType}=nothing
)
```

set_playを使用すると、ThingTypeにロールタイプを設定でき、古いものの代わりに新しいRoleTypeを設定することが可能です。ただし、これはインスタンス化されていないタイプにのみ許可されているため注意してください。
