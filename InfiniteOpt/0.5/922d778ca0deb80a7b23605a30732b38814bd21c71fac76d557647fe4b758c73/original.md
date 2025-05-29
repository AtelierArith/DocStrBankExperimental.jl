```
InfiniteOpt.ifelse(cond::NLPExpr, v1::Union{AbstractInfOptExpr, Real}, 
                   v2::Union{AbstractInfOptExpr, Real})::NLPExpr
```

A symbolic version of `Core.ifelse` that can be used to establish symbolic  expressions with logic conditions. Note that is must be written  `InfiniteOpt.ifelse` since it conflicts with `Core.ifelse`.

**Example**

```julia
julia> InfiniteOpt.ifelse(x >= y, 0, y^3)
ifelse(x >= y, 0, y^3)
```
