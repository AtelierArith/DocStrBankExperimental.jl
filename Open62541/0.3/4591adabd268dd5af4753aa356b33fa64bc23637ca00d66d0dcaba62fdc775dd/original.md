```
UA_Guid_equal(p1::Ptr{Open62541.UA_Guid}, p2::Ptr{Open62541.UA_Guid})::Bool
```

compares `p1` and `p2` and returns `true` if they are equal. Also works  with the corresponding high-level types (`JUA_xxx`) if they have been  defined.
