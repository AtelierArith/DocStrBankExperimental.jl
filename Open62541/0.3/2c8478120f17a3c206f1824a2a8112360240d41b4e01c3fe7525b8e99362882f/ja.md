```julia
struct UA_ReferenceTypeNode
```

フィールド:

  * `head::Open62541.UA_NodeHead`
  * `isAbstract::Bool`
  * `symmetric::Bool`
  * `inverseName::Open62541.UA_LocalizedText`
  * `referenceTypeIndex::UInt8`
  * `subTypes::Open62541.UA_ReferenceTypeSet`
