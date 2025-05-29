```
AbstractGateSymbol
```

A `GateSymbol` is an instantiation of an `AbstractGateSymbol`. It can be passed as an argument to a `Gate` [constuctor](https://docs.julialang.org/en/v1/manual/constructors/), where a `Gate` is also associated with `target` qubits. A `Gate` will be placed on those `target_qubits` if it is added to a `QuantumCircuit`. `AbstractGateSymbol` is useful for dispatching all the `GateSymbols` to default implementations of functions such as [`get_connected_qubits()`](@ref). Those functions can be specialized for `GateSymbols` requiring a different implementation. 

`AbstractGateSymbol` is an abstract type, which means that it cannot be instantiated.  Each concrete type of `GateSymbols` is a struct which is a subtype of `AbstractGateSymbol`. Each descendant of `AbstractGateSymbol` must implement at least the following methods:

  * `get_operator(gate::AbstractGateSymbol, T::Type{<:Complex}=ComplexF64})::AbstractOperator`
  * `get_num_connected_qubits(gate::AbstractGateSymbol)::Integer`

# Examples

A struct must be defined for each new `GateSymbol` type. The following X_45 `GateSymbol` applies a $45°$ rotation about the $X$ axis:

```jldoctest gate_struct
julia> struct X45 <: AbstractGateSymbol
       end;
```

We need to define how many connected qubits are needed for our new `GateSymbol`:

```jldoctest gate_struct
julia> Snowflurry.get_num_connected_qubits(::X45) = 1

```

A `Gate` constructor must be defined as

```jldoctest gate_struct
julia> x_45(target::Integer) = Gate(X45(), [target]);
```

along with an `Operator` constructor, with default precision `ComplexF64`, which is defined as

```jldoctest gate_struct
julia> x_45(T::Type{<:Complex} = ComplexF64) = rotation_x(π/4, T);

```

To simulate the effects of the gate in a `QuantumCircuit` or when applied to a `Ket`, the function `get_operator` must be extended:

```jldoctest gate_struct
julia> function Snowflurry.get_operator(gate::X45, T::Type{<:Complex} = ComplexF64)
          return rotation_x(π/4, T)
       end

```

The gate inverse can also be specified by extending the `inv` function:

```jldoctest gate_struct
julia> Base.inv(::X45) = Snowflurry.RotationX(-π/4);

```

An instance of the `X_45` `Gate` can now be created, along with its inverse:

```jldoctest gate_struct
julia> x_45_gate = x_45(1)
Gate Object: X45
Connected_qubits	: [1]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.9238795325112867 + 0.0im    0.0 - 0.3826834323650898im
0.0 - 0.3826834323650898im    0.9238795325112867 + 0.0im


julia> inv(x_45_gate)
Gate Object: Snowflurry.RotationX
Parameters: 
theta	: -0.7853981633974483

Connected_qubits	: [1]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.9238795325112867 + 0.0im    -0.0 + 0.3826834323650898im
-0.0 + 0.3826834323650898im    0.9238795325112867 + 0.0im


```

To enable the printing of a `QuantumCircuit` containing our new `GateSymbol` type, a display symbol must be defined as follows:

```jldoctest gate_struct
julia> Snowflurry.gates_display_symbols[X45] = ["X45"];

```

If this `Gate` will be sent as an instruction to a hardware QPU,  an instruction `String` must be defined:

```jldoctest gate_struct
julia> Snowflurry.instruction_symbols[X45] = "x45";

```

A circuit containing this `Gate` can now be constructed:

```jldoctest gate_struct
julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [x_45_gate])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──X45──

q[2]:───────

```

In addition, a `Controlled{X45}` gate can be constructed using:

```jldoctest gate_struct
julia> control = 1; target = 2;

julia> controlled(x_45(target), [control])
Gate Object: Controlled{X45}
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.9238795325112867 + 0.0im    0.0 - 0.3826834323650898im
0.0 + 0.0im    0.0 + 0.0im    0.0 - 0.3826834323650898im    0.9238795325112867 + 0.0im

```
