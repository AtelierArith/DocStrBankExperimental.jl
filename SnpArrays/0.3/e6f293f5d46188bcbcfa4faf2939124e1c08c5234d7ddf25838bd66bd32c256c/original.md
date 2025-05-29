```
kinship_pruning(grm::Matrix; method=:bottom_up, cutoff=0.125, min_samples=0)
```

Return a BitVector indicating which samples remains after kinship pruning.  Valid values for `method` are `:bottom_up`, `:top_down`, `:gcta`, and `:plink`. When `min_samples` is defined, pruning stops if that number of samples remain.

  * `:bottom_up` runs bottom-up greedy method, iteratively eliminating neighbors of sample with the lowest degree.
  * `:top_down` runs top-down greedy method, iteratively eliminating sample with the highest degree.
  * `:gcta` runs the method implemented in GCTA.
  * `:plink` runs the method implemented in PLINK.

In general, `:bottom_up` greedy method performs the best (keeping the hightest number of subjects) and has a guaranteed approximamtion ratio. With `min_samples` defined, `:top_down` greedy method keeps the least number of off-diagonal values.
