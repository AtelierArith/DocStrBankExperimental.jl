```
get_gradient(amp::AbstractManoptProblem, p)
get_gradient!(amp::AbstractManoptProblem, X, p)
```

[`AbstractManoptProblem`](@ref) `amp` の点 `p` での勾配を評価します。

評価は `!` バリアントのために `X` の場所で行われます。
