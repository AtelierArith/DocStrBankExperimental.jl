```
CollisionModel()
```

[`PLR_SimulationParameters`](@ref) または [`PLR_Simulation`](@ref) をインスタンス化する際に `plr_func` として使用される型で、PHY 抽象のための衝突モデルを模倣します。

!!! note
    `CollisionModel` のインスタンスは、他のすべての `plr_func` 値のように呼び出すことはできません。衝突モデルは、シミュレーションを実行する内部コード内に直接実装されています。

