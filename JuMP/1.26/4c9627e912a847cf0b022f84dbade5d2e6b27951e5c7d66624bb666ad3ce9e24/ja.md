```
termination_status(model::GenericModel)
```

ソルバーが停止した理由を説明する [`MOI.TerminationStatusCode`](@ref) を返します（すなわち、[`MOI.TerminationStatus`](@ref) 属性）。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> termination_status(model)
OPTIMIZE_NOT_CALLED::TerminationStatusCode = 0
```
