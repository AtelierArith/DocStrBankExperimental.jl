```
merge_coverage_counts(a1::Vector{CovCount}, a2::Vector{CovCount}) -> Vector{CovCount}
```

2つの行カバレッジカウントのベクターを与えられた場合、結果を合計し、両方がnullの場合はnullカウントを保持します。
