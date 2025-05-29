```
merge_coverage_counts(as::Vector{CovCount}...) -> Vector{CovCount}
```

行カバレッジカウントのベクトルを与えられた場合、結果を合計し、両方がnullの場合はnullカウントを保持します。
