```
get_num_qubits(x::AbstractOperator)
```

`Operator`に関連付けられた量子ビットの数を返します。

# 例

```jldoctest
julia> ρ = DenseOperator([1. 0. 
                          0. 0.])
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im

julia> get_num_qubits(ρ)
1

```
