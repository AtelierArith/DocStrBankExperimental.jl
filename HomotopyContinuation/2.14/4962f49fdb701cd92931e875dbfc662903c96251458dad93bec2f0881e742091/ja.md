```
OverdeterminedTracker(tracker::AbstractPathTracker, F::RandomizedSystem)
```

与えられた [`AbstractPathTracker`](@ref) `tracker` をラップし、各パス結果に対して与えられたランダム化システム `F` に対して [`excess_solution_check`](@ref) を適用します。
