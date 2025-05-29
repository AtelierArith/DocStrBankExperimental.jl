```
check(
    φ::Formula,
    s::AbstractInterpretationSet,
    args...;
    kwargs...
)::Vector{Bool}
```

[`AbstractInterpretationSet`](@ref) のすべてのインスタンスで式をチェックします。

[`AbstractInterpretationSet`](@ref) および [`Formula`](@ref) も参照してください。
