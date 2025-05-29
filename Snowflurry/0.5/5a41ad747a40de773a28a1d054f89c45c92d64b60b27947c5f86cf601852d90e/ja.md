```
get_gate_parameters(gate::AbstractGateSymbol)::Dict{String,Real}
```

`gate`の各パラメータの名前と値を含む`Dict`を返します。

# 例

```jldoctest
julia> get_gate_parameters(get_gate_symbol(universal(1, π/2, π/4, -π/3)))
Dict{String, Float64} with 3 entries:
  "theta"  => 1.5708
  "phi"    => 0.785398
  "lambda" => -1.0472

```
