```
ScoredTestSet([description])
```

Collection of [`ScoredTest`](@ref)s and [`ScoredTestSet`](@ref)s.

For adding new tests or testsets, use `*=` operand, e.g.

```julia
ts2 = ScoredTestSet("Subgroup of tests")
ts2 *= @scoredtest π < 3
ts2 *= @scoredtest π ≈ 3.1415

ts = ScoredTestSet("Main group")
ts *= @scoredtest 1 + 1 == 2
ts *= ts2
```
