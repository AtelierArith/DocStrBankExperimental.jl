```
vargmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

Return the index of the arguments which maximize `f` : ℝᴺ → ℝ over the dimensions `dims`. This expands upon the functionality which exists in Julia Base.
