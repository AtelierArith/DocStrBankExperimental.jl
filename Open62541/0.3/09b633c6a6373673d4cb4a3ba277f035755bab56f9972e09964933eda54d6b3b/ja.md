```
Open62541.UA_StructureField_copy(src::Ptr{Open62541.UA_StructureField}, dst::Ptr{Open62541.UA_StructureField})::UA_STATUSCODE
Open62541.UA_StructureField_copy(src::Open62541.UA_StructureField, dst::Ptr{Open62541.UA_StructureField})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容を宛先オブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
