```
Gate <: AbstractInstruction
```

`Gate` は `AbstractInstruction` の実装であり、`AbstractGateSymbol` とその `QuantumCircuit` 内での配置を指定します。この配置は、`Gate` が作用するターゲット量子ビット（または量子ビット群）に対応します。

# 例

```jldoctest
julia> gate = iswap(1, 2)
Gate Object: Snowflurry.ISwap
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.SwapLikeOperator:
Underlying data ComplexF64:
Equivalent DenseOperator:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im
```

```jldoctest
julia> gate = universal(3, pi/2, -pi/2, pi/2)
Gate Object: Snowflurry.Universal
Parameters:
theta	: 1.5707963267948966
phi	: -1.5707963267948966
lambda	: 1.5707963267948966

Connected_qubits	: [3]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.7071067811865476 + 0.0im    -4.329780281177466e-17 - 0.7071067811865475im
4.329780281177466e-17 - 0.7071067811865475im    0.7071067811865476 + 0.0im
```
