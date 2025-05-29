```julia
struct UA_ContentFilterElement
```

Fields:

  * `filterOperator::Open62541.UA_FilterOperator`
  * `filterOperandsSize::UInt64`
  * `filterOperands::Ptr{Open62541.UA_ExtensionObject}`
