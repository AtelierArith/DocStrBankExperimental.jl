```
constraint_pipe_flow(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

現在、`AbstractNCModel`型のモデルに対しては何も行われません。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`は流れが制限されるパイプのインデックス、`q_max_reverse`は流れが負の方向に移動する際の*最大*（負の）流量、つまり負の方向に移動する際の*最小*流量の大きさに対応し、`q_min_forward`は流れが正の（前方）方向に移動する際の*最小*（正の）流量です。`AbstractNCModel`型の場合、制約は追加されません。これらの定式化タイプでは、流れは方向によって分割されず、流量の境界は[`variable_flow`](@ref)での変数の初期化時に課されます。
