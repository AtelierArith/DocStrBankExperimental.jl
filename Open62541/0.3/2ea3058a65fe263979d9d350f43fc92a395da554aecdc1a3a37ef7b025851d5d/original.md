```julia
struct UA_NodePointer
```

Fields:

  * `immediate`
  * `id`
  * `expandedId`
  * `node`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
