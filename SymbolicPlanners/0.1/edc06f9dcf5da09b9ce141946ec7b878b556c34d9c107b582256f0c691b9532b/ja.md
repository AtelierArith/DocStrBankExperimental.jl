```julia
AStarPlanner(heuristic; kwargs...)

```

A*探索。最も低い$f$値を持つノードが最初に展開されます。これは、`heuristic`が許容可能であれば、コスト最適な解を生成することが保証されています。
