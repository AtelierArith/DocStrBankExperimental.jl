```
QuantumObjectEvolution(op::QuantumObject, f::Function, α::Union{Nothing,Number}=nothing; type = nothing)
QobjEvo(op::QuantumObject, f::Function, α::Union{Nothing,Number}=nothing; type = nothing)
```

Generate [`QuantumObjectEvolution`](@ref).

# Notes

  * The `f` parameter is used to pre-apply a function to the operators before converting them to SciML operators. The `type` parameter is used to specify the type of the [`QuantumObject`](@ref), either `Operator` or `SuperOperator`.
  * `QobjEvo` is a synonym of `QuantumObjectEvolution`.

# Examples

```jldoctest
julia> a = tensor(destroy(10), qeye(2))

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 18 stored entries:
⎡⠀⠑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠀⠑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠀⠑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠀⠑⎦

julia> coef(p, t) = exp(-1im * t)
coef (generic function with 1 method)

julia> op = QobjEvo(a, coef)

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20)
```
