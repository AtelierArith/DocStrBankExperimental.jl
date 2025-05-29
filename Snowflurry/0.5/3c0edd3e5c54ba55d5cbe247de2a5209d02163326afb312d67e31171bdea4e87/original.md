```
submit_job(
    client::Client,
    circuit::QuantumCircuit,
    shot_count::Integer,
    project_id::String,
    machine_name::String
)
```

Use a `client` to submit a `circuit` to a QPU service on the host server.  The QPU service is specified by the `machine_name`. The number of circuit executions is specified by `shot_count`. 

Returns the circuit ID, which can then be used when calling [`get_status`](@ref).

# Example

```jldoctest mylabel
julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1),
            readout(1, 1)]
        );

julia> submit_job(client, circuit, 100, "project_id", "yukon")
"8050e1ed-5e4c-4089-ab53-cccda1658cd0"

```
