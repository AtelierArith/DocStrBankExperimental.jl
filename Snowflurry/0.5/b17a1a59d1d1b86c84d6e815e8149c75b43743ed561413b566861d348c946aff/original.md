```
Controlled{G<:AbstractGateSymbol}<:AbstractGateSymbol
```

The `Controlled` object allows the construction of a controlled `AbstractGateSymbol` using an `Operator`  (the `kernel`) and the corresponding number of control qubits. A helper function, `controlled` can be used to easily create both controlled `AbstractGateSymbol`s and controlled `Gate`s. A call to `apply_gate` will be dispatched to the optimized routine if it exists. Otherwise, it will fall back to casting the operator into the equivalent `DenseOperator` and applying the created operator.

# Examples

We can use the `controlled` function to create a controlled-Hadamard gate:

```jldoctest controlled_hadamard
julia> controlled_hadamard = controlled(hadamard(2), [1])
Gate Object: Controlled{Snowflurry.Hadamard}
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.7071067811865475 + 0.0im    0.7071067811865475 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.7071067811865475 + 0.0im    -0.7071067811865475 + 0.0im

```

It can then be used in a `QuantumCircuit` as any other `Gate`, and its display symbol is  inherited from the display symbol of the single-target `Hadamard` `Gate`:

```jldoctest controlled_hadamard
julia> circuit=QuantumCircuit(qubit_count=2,instructions = [controlled_hadamard])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──*──
       |  
q[2]:──H──
          
```

In general, a `Controlled` struct with an arbitraty number of targets and controls can be  constructed. For instance, the following example constructs the equivalent of a `Toffoli` `Gate`,  but as a `ConnectedGate{SigmaX}` with `control_qubits=[1,2]` and `target_qubit=[3]`:

```jldoctest
julia> toffoli_as_controlled_gate = controlled(sigma_x(3), [1, 2])
Gate Object: Controlled{Snowflurry.SigmaX}
Connected_qubits	: [1, 2, 3]
Operator:
(8, 8)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
```
