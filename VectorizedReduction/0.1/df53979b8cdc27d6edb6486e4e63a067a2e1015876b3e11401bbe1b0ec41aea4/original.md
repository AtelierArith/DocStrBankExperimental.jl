```
vfindmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

Return the value and index of the arguments which maximize `f` : ℝᴺ → ℝ over the dimensions `dims`. This expands upon the functionality which exists in Julia Base.
