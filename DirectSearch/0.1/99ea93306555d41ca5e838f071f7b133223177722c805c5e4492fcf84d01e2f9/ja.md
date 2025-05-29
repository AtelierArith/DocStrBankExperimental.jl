```
AddExtremeConstraint(p::AbstractProblem, c::Vector{Function}; index::CollectionIndex=CollectionIndex(1))
```

極端なバリア制約を定義する関数のグループを登録します。各関数に対して個別に[`AddExtremeConstraint`](@ref)を呼び出します。
