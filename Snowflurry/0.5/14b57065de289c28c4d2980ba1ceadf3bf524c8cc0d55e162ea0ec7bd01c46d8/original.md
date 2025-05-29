```
serialize_job(circuit::QuantumCircuit,shot_count::Integer,host::String)
```

Creates a JSON-formatted string that contains the circuit configuration that will be sent  to a `QPU` service. The URL for the `QPU` service corresponds to `host` while the number of circuit executions is equal to `shot_count`.

!!! note
    Qubit and bit indices use zero-based indexing in the JSON encoding.


# Examples

```jldoctest
julia> c = QuantumCircuit(
            qubit_count = 2,
            instructions = [sigma_x(1)],
            name = "sigma_x job"
        )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          
julia> serialize_job(c, 10, "machine", "project_id")
"{\"shotCount\":10,\"name\":\"sigma_x job\",\"machineName\":\"machine\",\"projectID\":\"project_id\",\"type\":\"circuit\",\"circuit\":{\"operations\":[{\"parameters\":{},\"type\":\"x\",\"qubits\":[0]}],\"bitCount\":2,\"qubitCount\":2}}"
```
