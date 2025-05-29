```julia
MLJTreeParzenSpace(
    input_space::Dict{Symbol},
    suggestion::Dict{Symbol}
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenSpace

```

上記のように、`suggestion` にパラメータ名と特定の値を受け入れることもできます。これは調整される関数を評価するためのものです。

デフォルトのコンストラクタは、提案のベクターを受け入れます。

例（単一の提案）：

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    ),
    Dict(:num_layers => 3, :num_nodes => 40.0)
);
```

例（複数の提案）：

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    ),
    [
        Dict(:num_layers => 3, :num_nodes => 40.0),
        Dict(:num_layers => 3, :num_nodes => 30.0),
    ]
);
```
