```
print_connectivity(qpu::AbstractQPU, io::IO = stdout)
```

Prints the qubit connectivity of the `qpu` to `io`.

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


julia> print_connectivity(qpu)
1──2──3──4──5──6

```
