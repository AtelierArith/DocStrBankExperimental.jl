```
vtmapreduce(f, op, init, As::Vararg{AbstractArray, N}; dims=:, init) where {N}
```

Version for `f` : ℝᴺ → ℝ, with reduction over `dims`. Threaded.
