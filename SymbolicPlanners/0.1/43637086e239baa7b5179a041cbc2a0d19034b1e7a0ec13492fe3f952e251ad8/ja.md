```
PrecomputedHeuristic(heuristic::Heuristic, args...)
```

既存の `heuristic` をラップし、それが事前に計算されていることを保証し、[`precompute!`](@ref) への後続の呼び出しでの繰り返しの事前計算を防ぎます。
