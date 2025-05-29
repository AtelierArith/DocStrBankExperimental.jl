```
vvmapreduce(f, op, init, As::Vararg{AbstractArray, N}) where {N}
```

Version of mapreduce for `f` : ℝᴺ → ℝ, with reduction occurring over all dimensions.
