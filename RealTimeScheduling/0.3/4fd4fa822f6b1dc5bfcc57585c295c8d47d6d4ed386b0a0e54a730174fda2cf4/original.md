```
MissAny([T=Int, ]miss, window)
```

Construct a [`MeetAny{T}`](@ref) constraint that allows at most `miss` deadlines to be missed in any window of size `window`.

While constraints of this sort are often expressed as a different type in the literature, they are equivalent to [`MeetAny`](@ref), so using a single type simplifies any code using weakly hard constraints.
