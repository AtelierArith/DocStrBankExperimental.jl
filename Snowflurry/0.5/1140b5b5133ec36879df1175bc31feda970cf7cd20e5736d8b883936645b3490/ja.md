```
is_native_instruction(
    gate::Union{Gate},
    connectivity::Union{LineConnectivity,LatticeConnectivity},
    native_gates::Vector{DataType} = set_of_native_gates,
)::Bool
```

`gate`が`connectivity`および可能な`native_gates`のリストに対するネイティブ命令である場合、`true`を返します。Anyon QPUのネイティブゲートがデフォルトで使用されます。

ネイティブ命令は、`native_gates`に含まれ、`connectivity`を満たす命令として定義されます。`gate`が`connectivity`の`excluded_positions`または`excluded_connections`に配置されているかどうかは確認しません。ゲートは3つ未満のキュービットで動作する必要があります。

# 例

```jldoctest
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> is_native_instruction(control_z(1, 2), connectivity)
true

julia> is_native_instruction(control_z(1, 3), connectivity)
false

julia> is_native_instruction(control_x(1, 2), connectivity)
false

julia> is_native_instruction(control_x(1, 2), connectivity, [Snowflurry.ControlX])
true

julia> is_native_instruction(toffoli(1, 2, 3), connectivity, [Snowflurry.Toffoli])
false

```
