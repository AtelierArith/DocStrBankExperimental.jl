```
Open62541.UA_StructureDescription_copy(src::Ptr{Open62541.UA_StructureDescription}, dst::Ptr{Open62541.UA_StructureDescription})::UA_STATUSCODE
Open62541.UA_StructureDescription_copy(src::Open62541.UA_StructureDescription, dst::Ptr{Open62541.UA_StructureDescription})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容を宛先オブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
