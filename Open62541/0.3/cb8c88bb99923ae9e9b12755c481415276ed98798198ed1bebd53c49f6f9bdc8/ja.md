```
Open62541.UA_ModifySubscriptionRequest_copy(src::Ptr{Open62541.UA_ModifySubscriptionRequest}, dst::Ptr{Open62541.UA_ModifySubscriptionRequest})::UA_STATUSCODE
Open62541.UA_ModifySubscriptionRequest_copy(src::Open62541.UA_ModifySubscriptionRequest, dst::Ptr{Open62541.UA_ModifySubscriptionRequest})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
