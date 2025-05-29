```julia
MLJTreeParzenSpace(
    input_space::Dict{Symbol}
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenSpace

```

`input_space`を使用して、パラメータ名をキー、`TreeParzen.HP.*` 調整可能な分布（またはこれらの合成式）を値とするハイパーパラメータ検索空間を構築します。

例：

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    )
);
```
