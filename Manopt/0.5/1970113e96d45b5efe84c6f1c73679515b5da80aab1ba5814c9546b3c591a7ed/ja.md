```
get_objective(mp::AbstractManoptProblem, recursive=false)
```

[`AbstractManifoldObjective`](@ref) を [`AbstractManoptProblem`](@ref) 内に格納された目的関数として返します。`recursive` が true に設定されている場合、目的関数のすべてのデコレーターも追加でアンラップします。
