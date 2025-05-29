```
vargmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

Return the index of the arguments which minimize `f` : ℝᴺ → ℝ over the dimensions `dims`. Threaded.
