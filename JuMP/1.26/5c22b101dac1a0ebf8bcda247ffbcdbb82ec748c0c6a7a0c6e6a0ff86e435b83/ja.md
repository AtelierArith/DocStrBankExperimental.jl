```
primal_status(model::GenericModel; result::Int = 1)
```

最近のプライマルソリューションのステータスを説明する [`MOI.ResultStatusCode`](@ref) を返します（つまり、結果インデックス `result` に関連付けられた [`MOI.PrimalStatus`](@ref) 属性）。

関連情報: [`result_count`](@ref)。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> primal_status(model; result = 2)
NO_SOLUTION::ResultStatusCode = 0
```
