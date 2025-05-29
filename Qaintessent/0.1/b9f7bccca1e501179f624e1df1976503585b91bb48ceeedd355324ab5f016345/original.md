```
sparse_matrix(cg::CircuitGate{M,G}, N::Integer=0) where {M,G <: AbstractGate}
```

returns matrix representation of a [CircuitGate](@ref) object that can applied to a state vector of `N` qubits. `N` can be

# Examples

```jldoctest
julia> cg = circuit_gate(2, Y, 1);
julia> sparse_matrix(cg)
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 4 stored entries:
  [1, 1]  =  1.0+0.0im
  [4, 2]  =  0.0+1.0im
  [3, 3]  =  1.0+0.0im
  [2, 4]  =  0.0-1.0im
```
