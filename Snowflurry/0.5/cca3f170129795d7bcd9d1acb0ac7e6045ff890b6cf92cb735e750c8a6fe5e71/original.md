```
run_job(qpu::VirtualQPU, circuit::QuantumCircuit, shot_count::Integer)
```

Execute a circuit on a `QPU` simulator. The number of circuit executions is specified by `shot_count`.

Returns a histogram of the circuit measurement outcomes as prescribed by the `Readout` instructions in the `circuit`.

# Example

```jldoctest; filter =  r", [0-9]+" => ", 147"
julia> qpu = VirtualQPU();

julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [
                sigma_x(3),
                control_z(2, 1),
                readout(1, 1),
                readout(2, 2),
                readout(3, 3)
            ]
        );

julia> run_job(qpu, circuit, 100)
(Dict("001" => 100), 147)

```
