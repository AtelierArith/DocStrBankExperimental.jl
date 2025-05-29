```
is_native_instruction(
    readout::Readout,
    connectivity::Union{LineConnectivity,LatticeConnectivity},
    native_gates::Vector{DataType} = set_of_native_gates,
)::Bool
```

`readout`が接続性を満たす場合、`true`を返します。

接続性の`excluded_positions`に`gate`が配置されているかどうかは確認しません。

# 例

```jldoctest
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> is_native_instruction(readout(2, 2), connectivity)
true

julia> is_native_instruction(readout(4, 4), connectivity)
false

```
