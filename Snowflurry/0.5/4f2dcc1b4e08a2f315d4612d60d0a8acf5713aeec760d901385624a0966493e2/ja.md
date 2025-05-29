```
get_num_bodies(x::AbstractOperator, hilbert_space_size_per_body=2)
```

`hilbert_space_size_per_body`に対して与えられた`Operator`に関連付けられたボディの数を返します。

# 例

```jldoctest
julia> ρ = DenseOperator([1. 0. 0.
                          0. 0. 0.
                          0. 0. 0.])
(3, 3)-要素 Snowflurry.DenseOperator:
基礎データ ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im

julia> get_num_bodies(ρ, 3)
1

```
