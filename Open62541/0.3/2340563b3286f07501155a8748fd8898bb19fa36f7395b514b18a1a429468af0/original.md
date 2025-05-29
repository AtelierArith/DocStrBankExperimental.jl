```julia
struct UA_Node
```

Fields:

  * `head`
  * `variableNode`
  * `variableTypeNode`
  * `methodNode`
  * `objectNode`
  * `objectTypeNode`
  * `referenceTypeNode`
  * `dataTypeNode`
  * `viewNode`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
