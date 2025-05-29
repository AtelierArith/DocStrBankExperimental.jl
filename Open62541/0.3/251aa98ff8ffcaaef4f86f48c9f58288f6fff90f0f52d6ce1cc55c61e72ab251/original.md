```
request::Ptr{UA_CreateSubscriptionRequest} = UA_CreateSubscriptionRequest_default()
```

create a subscription create request to which monitored items can be added subsequently. The subscription properties are set to their default values.

Note that memory for the response is allocated by C and needs to be cleaned up by using `UA_CreateSubscriptionRequest_delete(request)` after its use.

See also:

[`UA_CreateSubscriptionRequest`](@ref)
