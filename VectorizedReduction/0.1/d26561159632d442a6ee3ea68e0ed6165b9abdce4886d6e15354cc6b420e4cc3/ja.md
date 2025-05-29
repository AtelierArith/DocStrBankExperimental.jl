```
vvmapreduce(f, op, init, As::Tuple{Vararg{AbstractArray}}, dims=:)
```

与えられた `dims` に対する削減を伴う `f` : ℝᴺ → ℝ のための mapreduce のバージョン。
