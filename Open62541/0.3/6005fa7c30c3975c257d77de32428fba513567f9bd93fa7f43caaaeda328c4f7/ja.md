```
Open62541.UA_DeleteSubscriptionsRequest_copy(src::Ptr{Open62541.UA_DeleteSubscriptionsRequest}, dst::Ptr{Open62541.UA_DeleteSubscriptionsRequest})::UA_STATUSCODE
Open62541.UA_DeleteSubscriptionsRequest_copy(src::Open62541.UA_DeleteSubscriptionsRequest, dst::Ptr{Open62541.UA_DeleteSubscriptionsRequest})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
