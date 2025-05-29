```
sparse_matrix(cgs::Vector{<:CircuitGate}, N::Integer=0)
```

returns matrix representation of a `Vector{<:CircuitGate}` object that can applied to a state vector of `N` qubits.

# Examples

```jldoctest
julia> cgs = CircuitGate[
                circuit_gate(2, Y, 1),
                circuit_gate(2, Z),
                circuit_gate(1, HadamardGate())
                ];
julia> sparse_matrix(cgs)
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 8 stored entries:
  [1, 1]  =  0.707107+0.0im
  [2, 1]  =  0.707107+0.0im
  [3, 2]  =  0.0-0.707107im
  [4, 2]  =  0.0+0.707107im
  [3, 3]  =  -0.707107+0.0im
  [4, 3]  =  -0.707107+0.0im
  [1, 4]  =  0.0-0.707107im
  [2, 4]  =  0.0+0.707107im
```
