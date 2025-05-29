```
primal_status(model::Model; result::Int = 1)
```

最近のプライマルソリューションのステータスを説明する [`MOI.ResultStatusCode`](@ref) を返します（すなわち、結果インデックス `result` に関連付けられた [`MOI.PrimalStatus`](@ref) 属性）。

関連情報: [`result_count`](@ref).
