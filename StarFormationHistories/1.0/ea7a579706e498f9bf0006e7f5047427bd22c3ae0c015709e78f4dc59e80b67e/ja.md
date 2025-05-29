```
fit_templates(models::AbstractMatrix{S},
              data::AbstractVector{<:Number};
              x0::AbstractVector{<:Number} = ones(S,length(models)),
              kws...) where S <: Number
```

この呼び出しシグネチャは、`models` と `data` のフラット化された形式をサポートしています。詳細については、[`StarFormationHistories.composite!`](@ref) のフラット化された呼び出しシグネチャに関するノートを参照してください。
