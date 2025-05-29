```
update_fitness!([f], eval::Evaluator, candidate::Candidate; force::Bool=false) -> Candidate
```

Calculate fitness of `candidate` and optionally apply `f`. `force` specifies whether to re-evaluate fitness, if the candidate already has non-NA one.
