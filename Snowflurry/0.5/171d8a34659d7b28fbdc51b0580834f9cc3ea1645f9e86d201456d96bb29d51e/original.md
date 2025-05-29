```
transpile_and_run_job(
    qpu::UnionAnyonQPU,
    circuit::QuantumCircuit,
    shot_count::Integer;
    transpiler::Transpiler = get_transpiler(qpu)
)
```

This method first transpiles the input circuit using either the default transpiler, or any other transpiler passed as a keyword argument. The transpiled circuit is then submitted for execution on an Anyon QPU. The number of circuit executions is specified by `shot_count`.

Returns the histogram of the circuit measurement outcomes along with the job's  execution time on the `QPU` (in milliseconds), or an error message.

# Example

```jldoctest
julia> qpu = AnyonYukonQPU(client_anyon, "project_id");

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(3),
                        control_z(2, 1),
                        readout(3, 3)
                    ]);

julia> transpile_and_run_job(qpu, circuit, 100)
(Dict("001" => 100), 542)

```
