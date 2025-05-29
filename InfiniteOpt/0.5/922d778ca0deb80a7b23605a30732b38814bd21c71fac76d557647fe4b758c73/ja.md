```
InfiniteOpt.ifelse(cond::NLPExpr, v1::Union{AbstractInfOptExpr, Real}, 
                   v2::Union{AbstractInfOptExpr, Real})::NLPExpr
```

論理条件を用いて象徴的な式を確立するために使用できる `Core.ifelse` の象徴的バージョンです。`Core.ifelse` と競合するため、`InfiniteOpt.ifelse` と書く必要があることに注意してください。

**例**

```julia
julia> InfiniteOpt.ifelse(x >= y, 0, y^3)
ifelse(x >= y, 0, y^3)
```
