```
tr(A::QuantumObject)
```

Returns the trace of [`QuantumObject`](@ref).

Note that this function only supports for [`Operator`](@ref) and [`SuperOperator`](@ref)

# Examples

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> tr(a' * a)
190.0 + 0.0im
```
