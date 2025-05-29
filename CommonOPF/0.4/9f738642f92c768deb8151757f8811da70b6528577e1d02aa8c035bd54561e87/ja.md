```
init_split_networks!(nets::Vector{Network{SinglePhase}}; init_vs::Dict = Dict())
```

上流の葉ノードの負荷を下流ノードのすべての負荷の合計に等しく設定します。`nets`の順序は、負荷の合計がすべての下流のサブツリーを考慮に入れるように、葉ブランチから幹ブランチへと進むことが重要です。

`init_vs`が提供されている場合、`net.v0`は`Input`に設定され、その`net.substation_bus`は`init_vs`のキーに等しくなります。

```julia
init_vs = Dict(
    "sub_bus_1" => 0.98
)

for net in nets
    if net.substation_bus in keys(init_vs)
        net.v0 = init_vs[net.substation_bus]
    end
end
```
