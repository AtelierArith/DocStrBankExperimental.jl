```
get_operator(gate::Gate)
```

`Gate`に関連付けられた`Operator`を返します。

# 例

```jldoctest
julia> x = sigma_x(1);

julia> get_operator(get_gate_symbol(x))
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


```
