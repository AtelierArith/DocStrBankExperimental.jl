```
get_objective(mp::AbstractManoptProblem, recursive=false)
```

[`AbstractManifoldObjective`](@ref) が [`AbstractManoptProblem`](@ref) に格納されている目的を返します。`recursive` が true に設定されている場合、目的のすべてのデコレーターも追加でアンラップします。
