```julia
struct UA_VariableTypeNode
```

Fields:

  * `head`
  * `dataType`
  * `valueRank`
  * `arrayDimensionsSize`
  * `arrayDimensions`
  * `valueBackend`
  * `valueSource`
  * `value`
  * `isAbstract`
  * `lifecycle`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
