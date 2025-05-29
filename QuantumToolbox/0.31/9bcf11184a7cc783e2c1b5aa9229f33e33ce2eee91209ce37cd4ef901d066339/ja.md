```
QuantumObjectEvolution(op::QuantumObject, f::Function, α::Union{Nothing,Number}=nothing; type = nothing)
QobjEvo(op::QuantumObject, f::Function, α::Union{Nothing,Number}=nothing; type = nothing)
```

[`QuantumObjectEvolution`](@ref)を生成します。

# 注意事項

  * `f` パラメータは、演算子を SciML 演算子に変換する前に関数を事前に適用するために使用されます。`type` パラメータは、[`QuantumObject`](@ref) のタイプを指定するために使用され、`Operator` または `SuperOperator` のいずれかです。
  * `QobjEvo` は `QuantumObjectEvolution` の同義語です。

# 例

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
