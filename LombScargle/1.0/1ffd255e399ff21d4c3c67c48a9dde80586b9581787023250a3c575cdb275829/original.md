```
fapinv(b::Bootstrap, prob::Real)
```

Return the power value whose false-alarm probability is `prob` in the bootstrap sample `b`.

It returns `NaN` if the requested probability is too low and the power cannot be determined with the bootstrap sample `b`.  In this case, you should enlarge your bootstrap sample so that `N*fap` can be rounded to an integer larger than or equal to 1.

This is the inverse of [`fap`](@ref) function.
