```julia
struct UA_NodeId
```

Fields:

  * `nameSpaceIndex`
  * `identifierType`
  * `identifier`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
