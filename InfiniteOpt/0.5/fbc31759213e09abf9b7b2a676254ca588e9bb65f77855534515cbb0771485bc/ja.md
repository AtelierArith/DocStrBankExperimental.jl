```
InfiniteModel([optimizer_constructor];
              [OptimizerModel::Function = TranscriptionModel,
              add_bridges::Bool = true, optimizer_model_kwargs...])
```

`optimizer_constructor`が指定されている場合、最適化子が指定された新しい無限モデルを返します。最適化子は後で[`JuMP.set_optimizer`](@ref)呼び出しで設定することもできます。デフォルトでは、`optimizer_model`データフィールドは[`TranscriptionModel`](@ref)で初期化されますが、拡張によって要求される場合は[`set_optimizer_model`](@ref)を介して異なるタイプのモデルを割り当てることができます。

**例**

```jldoctest
julia> using InfiniteOpt, JuMP, Ipopt;

julia> model = InfiniteModel()
An InfiniteOpt Model
Feasibility problem with:
Finite Parameters: 0
Infinite Parameters: 0
Variables: 0
Measures: 0
Derivatives: 0
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> model = InfiniteModel(Ipopt.Optimizer)
An InfiniteOpt Model
Feasibility problem with:
Finite Parameters: 0
Infinite Parameters: 0
Variables: 0
Measures: 0
Derivatives: 0
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: EMPTY_OPTIMIZER
Solver name: Ipopt
```
