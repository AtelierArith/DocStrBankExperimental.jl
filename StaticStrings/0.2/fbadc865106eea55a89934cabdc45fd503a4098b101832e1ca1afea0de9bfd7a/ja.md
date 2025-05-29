```
SubStaticString(data::NTuple{N, UInt8}, ind::Integer)
SubStaticString(data::NTuple{N, UInt8}, ind::AbstractUnitRange)
substatic"string"N
```

[`AbstractStaticString`](@ref) は、NTuple{N,UInt8} に最大 `N` コードユニットを格納します。実際に使用されるコードユニットは、AbstractUnitRange によって示されるサブセットです。
