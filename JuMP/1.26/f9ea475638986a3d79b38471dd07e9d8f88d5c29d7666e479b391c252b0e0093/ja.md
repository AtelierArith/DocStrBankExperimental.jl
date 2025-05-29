```
Model([optimizer_factory;] add_bridges::Bool = true)
```

JuMPモデルの新しいインスタンスを作成します。

`optimizer_factory`が提供されている場合、モデルは`MOI.instantiate(optimizer_factory)`によって返される最適化器で初期化されます。

`optimizer_factory`が提供されていない場合は、[`set_optimizer`](@ref)を使用して最適化器を設定してから[`optimize!`](@ref)を呼び出してください。

`add_bridges`がtrueの場合、JuMPは自動的に問題を最適化器がサポートする形式に再定式化するために[`MOI.Bridges.LazyBridgeOptimizer`](@ref)を追加します。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> solver_name(model)
"Ipopt"

julia> import HiGHS

julia> import MultiObjectiveAlgorithms as MOA

julia> model = Model(() -> MOA.Optimizer(HiGHS.Optimizer); add_bridges = false);
```
