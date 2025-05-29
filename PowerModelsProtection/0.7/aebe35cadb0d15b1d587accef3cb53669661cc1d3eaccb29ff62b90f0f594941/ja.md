```
build_fault_study(data::Dict; default_fault_resistance::Real=0.0001)
```

送電（単相正序）ネットワーク上の故障研究の辞書を構築します。これは[`solve_fault_study`](@ref solve_fault_study)と併用することを目的としています。

この関数はすべてのバスを反復処理し、デフォルトの故障抵抗を使用して故障を作成します。故障研究の辞書は次の構造を持ちます：

```julia
    Dict{String,Any}(
        "bus_i" => Dict{String,Any}(
            "fault_bus" => bus_i
            "gf" => 1 / resistance,
            "status" => 1
        ),
        ...
    )
```
