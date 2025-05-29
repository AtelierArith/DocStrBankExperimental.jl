```
Open62541.UA_SetMonitoringModeRequest_copy(src::Ptr{Open62541.UA_SetMonitoringModeRequest}, dst::Ptr{Open62541.UA_SetMonitoringModeRequest})::UA_STATUSCODE
Open62541.UA_SetMonitoringModeRequest_copy(src::Open62541.UA_SetMonitoringModeRequest, dst::Ptr{Open62541.UA_SetMonitoringModeRequest})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
