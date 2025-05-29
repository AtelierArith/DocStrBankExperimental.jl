```
merge_coverage_counts(as::Vector{CovCount}...) -> Vector{CovCount}
```

Given vectors of line coverage counts, sum together the results, preseving null counts if both are null.
