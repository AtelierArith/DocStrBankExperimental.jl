```
transpile_and_run_job(
    qpu::VirtualQPU,
    circuit::QuantumCircuit,
    shot_count::Integer;
    transpiler::Transpiler = get_transpiler(qpu)
)
```

This method first transpiles the input circuit using either the default transpiler, or any other transpiler passed as a keyword argument. The transpiled circuit is then executed on a `QPU` simulator, where the number of circuit executions is specified by `shot_count`.

Returns the histogram of the circuit measurement outcomes, or an error message.

# Example

```jldoctest; filter =  r", [0-9]+" => ", 132"
julia> qpu = VirtualQPU();

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(3),
                        control_z(2, 1),
                        readout(1, 1),
                        readout(2, 2),
                        readout(3, 3)
                    ]);

julia> transpile_and_run_job(qpu, circuit,100)
(Dict("001" => 100), 132)

```
