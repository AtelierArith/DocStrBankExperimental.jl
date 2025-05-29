```
get_subgradient(amp::AbstractManoptProblem, p)
get_subgradient!(amp::AbstractManoptProblem, X, p)
```

[`AbstractManoptProblem`](@ref) `amp` の点 `p` におけるサブグラディエントを評価します。

評価は `!` バリアントのために `X` の場所で行われます。結果は決定論的でない可能性があり、サブ微分の *1* 要素が返されます。
