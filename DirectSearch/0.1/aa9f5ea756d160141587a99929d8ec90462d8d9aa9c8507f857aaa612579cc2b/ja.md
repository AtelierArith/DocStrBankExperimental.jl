```
AddProgressiveConstraint(p::AbstractProblem, c::Vector{Function})::Vector{Int}
```

進行的バリア制約を定義する関数のグループを登録します。各関数に対して個別に[`AddProgressiveConstraint`](@ref)を呼び出します。
