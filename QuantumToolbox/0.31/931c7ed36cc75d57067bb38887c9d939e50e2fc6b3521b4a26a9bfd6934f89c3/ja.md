```
QobjEvo(op_func_list::Union{Tuple,AbstractQuantumObject}, α::Union{Nothing,Number}=nothing; type=nothing)
QuantumObjectEvolution(op_func_list::Union{Tuple,AbstractQuantumObject}, α::Union{Nothing,Number}=nothing; type=nothing)
```

[`QuantumObjectEvolution`](@ref)を生成します。

# 引数

  * `op_func_list::Union{Tuple,AbstractQuantumObject}`: タプルのタプルまたは演算子のリスト。
  * `α::Union{Nothing,Number}=nothing`: 演算子を前に掛けるスカラー。

!!! warning "型の安定性に注意！"
    QuTiPとは異なり、この関数は`op_func_list`を`Vector`型としてサポートしていないことに注意してください。これは型の安定性の問題に関連しています。詳細については、セクション[型の安定性の重要性](@ref doc:Type-Stability)を参照してください。


`α`が提供されると、`op_func_list`内のすべての演算子は`α`で前に掛けられます。`type`パラメータは、[`QuantumObject`](@ref)のタイプを指定するために使用され、`Operator`または`SuperOperator`のいずれかになります。`f`パラメータは、演算子をSciML演算子に変換する前に関数を前適用するために使用されます。

!!! note
    `QobjEvo`は`QuantumObjectEvolution`の同義語です。


# 例

この演算子は、QuTiPの`QobjEvo`オブジェクトと同じ方法で初期化できます。例えば

```jldoctest qobjevo
julia> a = tensor(destroy(10), qeye(2))

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 18 stored entries:
⎡⠀⠑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠀⠑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠀⠑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠀⠑⎦

julia> σm = tensor(qeye(10), sigmam())

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 10 stored entries:
⎡⠂⡀⠀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡀⠀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡀⠀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡀⎦

julia> coef1(p, t) = exp(-1im * t)
coef1 (generic function with 1 method)

julia> coef2(p, t) = sin(t)
coef2 (generic function with 1 method)

julia> op1 = QobjEvo(((a, coef1), (σm, coef2)))

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))
```

特定の時間`t`で演算子を具体化することもできます。

```jldoctest qobjevo
julia> op1(0.1)

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 28 stored entries:
⎡⠂⡑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡑⎦
```

パラメータ依存の時間発展もサポートしています。

```jldoctest qobjevo
julia> coef1(p, t) = exp(-1im * p.ω1 * t)
coef1 (generic function with 1 method)

julia> coef2(p, t) = sin(p.ω2 * t)
coef2 (generic function with 1 method)

julia> op1 = QobjEvo(((a, coef1), (σm, coef2)))

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))

julia> p = (ω1 = 1.0, ω2 = 0.5)
(ω1 = 1.0, ω2 = 0.5)

julia> op1(p, 0.1)

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 28 stored entries:
⎡⠂⡑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡑⎦
```
