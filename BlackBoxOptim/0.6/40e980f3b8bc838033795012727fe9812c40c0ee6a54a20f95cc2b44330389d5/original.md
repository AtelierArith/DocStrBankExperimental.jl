```
update_fitness!([f], eval::Evaluator, candidates; force::Bool=false)
```

Calculate fitness of `candidates` and optionally apply `f` to each processed one. `force` specifies if already existing non-NA fitnesses should be re-evaluated.
