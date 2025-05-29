```
run_job(qpu::AnyonYukonQPU, circuit::QuantumCircuit, shot_count::Integer)
```

Submit a circuit to a `QPU` service for execution. The function does not perform the standard transpilation as in [`transpile_and_run_job`](@ref). The number of circuit executions is specified by `shot_count`.

Returns a histogram of the circuit measurement outcomes along with the  simulation's execution time (in milliseconds) or an error message.

If the `circuit` is invalid, it is not sent to the host and an error is thrown. The `circuit` can be invalid for the following reasons:

  * The `circuit` contains no `Readout` instructions (see   [`CircuitContainsAReadoutTranspiler`](@ref)).
  * Multiple `Readout` instructions have the same destination bits (see   [`ReadoutsDoNotConflictTranspiler`](@ref)).
  * The `Readout` instructions are not the last operation on each qubit where a readout is   present (see [`ReadoutsAreFinalInstructionsTranspiler`](@ref)).
  * The `circuit` contains a `Controlled` gate that operates on more than two qubits (see   [`UnsupportedGatesTranspiler`](@ref)).

# Example

```jldoctest
julia> qpu = AnyonYukonQPU(client, "project_id")
Quantum Processing Unit:
   manufacturer:  Anyon Systems Inc.
   generation:    Yukon
   serial_number: ANYK202201
   project_id:    project_id
   qubit_count:   6 
   connectivity_type:  linear
   realm:         test-realm

julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1), readout(1, 1)]
        );

julia> run_job(qpu, circuit, 100)
(Dict("001" => 100), 542)

```
