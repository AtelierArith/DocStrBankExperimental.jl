```
get_num_gates_per_type(
    circuit::QuantumCircuit
)::AbstractDict{<: AbstractString, <:Integer}
```

Returns a dictionary listing the number of gates of each type found in the `circuit`.

The dictionary keys are the instruction symbols of the gates while the values are the number of gates found.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1), hadamard(2));

julia> push!(c, control_x(1, 2));

julia> push!(c, hadamard(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*───────
                 |       
q[2]:───────H────X────H──
                         



julia> get_num_gates_per_type(c)
Dict{String, Int64} with 2 entries:
  "h"  => 3
  "cx" => 1

```
