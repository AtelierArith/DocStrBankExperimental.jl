```
merge_coverage_counts(a1::Vector{CovCount}, a2::Vector{CovCount}) -> Vector{CovCount}
```

Given two vectors of line coverage counts, sum together the results, preseving null counts if both are null.
