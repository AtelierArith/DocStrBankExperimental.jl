```
AnyonYukonQPU <: AbstractQPU
```

A data structure that describes an Anyon System QPU of the Yukon generation.  The QPU contains 6 qubits in a linear arrangement (see [`LineConnectivity`](@ref)). 

# Fields

  * `client                  ::Client` – Client to the QPU server.
  * `status_request_throttle ::Function` – Used to limit the rate of job status requests.
  * `project_id              ::String` – Used to identify the project for the jobs that are sent to the QPU.
  * `realm                   ::String` – Optional: Used to identify the host server realm for the submission of requests.

# Example

```jldoctest
julia>  qpu = AnyonYukonQPU(
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
```
