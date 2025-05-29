```julia
struct UA_VariableNode
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
  * `accessLevel`
  * `minimumSamplingInterval`
  * `historizing`
  * `isDynamic`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
