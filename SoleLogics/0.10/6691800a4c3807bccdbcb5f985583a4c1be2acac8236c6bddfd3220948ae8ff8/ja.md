```
check(
    φ::Formula,
    s::AbstractInterpretationSet,
    i_instance::Integer,
    args...;
    kwargs...
)::Bool
```

[`AbstractInterpretationSet`](@ref)の$i$-番目のインスタンスで式をチェックします。

[`AbstractInterpretationSet`](@ref)や[`Formula`](@ref)も参照してください。
