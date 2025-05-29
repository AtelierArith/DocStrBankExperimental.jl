```julia
struct UA_DataType
```

フィールド:

  * `typeName`
  * `typeId`
  * `binaryEncodingId`
  * `memSize`
  * `typeKind`
  * `pointerFree`
  * `overlayable`
  * `membersSize`
  * `members`

この型はCでユニオン型として定義されているため、この型のPtrのフィールドを設定するには特別な注意が必要です。
