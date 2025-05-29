```
solver_name(model::GenericModel)
```

利用可能な場合、基盤となる最適化ツールの[`MOI.SolverName`](@ref)プロパティを返します。

最適化ツールが接続されていない場合、`AUTOMATIC`または`MANUAL`モードでは`"No optimizer attached."`を返します。

属性が実装されていない場合は、`"SolverName() attribute not implemented by the optimizer."`を返します。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> solver_name(model)
"Ipopt"

julia> model = Model();

julia> solver_name(model)
"No optimizer attached."

julia> model = Model(MOI.FileFormats.MPS.Model);

julia> solver_name(model)
"SolverName() attribute not implemented by the optimizer."
```
