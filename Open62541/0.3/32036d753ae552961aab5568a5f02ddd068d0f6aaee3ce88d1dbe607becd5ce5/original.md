```julia
struct UA_DataType
```

Fields:

  * `typeName`
  * `typeId`
  * `binaryEncodingId`
  * `memSize`
  * `typeKind`
  * `pointerFree`
  * `overlayable`
  * `membersSize`
  * `members`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
