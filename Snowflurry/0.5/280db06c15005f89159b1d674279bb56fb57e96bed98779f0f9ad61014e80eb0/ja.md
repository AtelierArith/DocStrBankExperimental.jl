```
get_gate_symbol(gate::Gate)::AbstractGateSymbol
```

`gate`に関連付けられたシンボルを返します。

# 例

```jldoctest
julia> gate = sigma_x(1);

julia> get_gate_symbol(gate)
Snowflurry.SigmaX()

```
