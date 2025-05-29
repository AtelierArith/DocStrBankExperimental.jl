```
vtfindmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

Return the value and index of the arguments which minimize `f` : ℝᴺ → ℝ over the dimensions `dims`. Threaded.
