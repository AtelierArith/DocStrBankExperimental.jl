```
anova(::Type{LRT}, <model>; kwargs...)
anova(::Type{LRT}, <models>...; kwargs...)
```

尤度比検定による分散分析。

`AnovaResult{M, LRT, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。
