```
get_client(qpu_service::UnionAnyonQPU)
```

Returns the client that is associated with the `qpu_service`.

# Example

```jldoctest
julia> qpu = AnyonYukonQPU(
           host = "http://example.anyonsys.com",
           user = "test_user",
           access_token = "not_a_real_access_token",
           project_id = "test-project",
           realm = "test-realm"
       )
Quantum Processing Unit:
   manufacturer:  Anyon Systems Inc.
   generation:    Yukon
   serial_number: ANYK202201
   project_id:    test-project
   qubit_count:   6
   connectivity_type:  linear
   realm:         test-realm


julia> get_client(qpu)
Client for QPU service:
   host:         http://example.anyonsys.com
   user:         test_user 
   realm:        test-realm 


```
