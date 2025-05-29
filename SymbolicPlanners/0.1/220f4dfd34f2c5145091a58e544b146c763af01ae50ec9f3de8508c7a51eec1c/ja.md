```julia
WeightedAStarPlanner(heuristic, h_mult; kwargs...)

```

重み付きA*探索は、ノードの$f$値を計算する際にヒューリスティック推定値に`h_mult`を掛けます。最も低い$f$値を持つノードが最初に展開されます。
