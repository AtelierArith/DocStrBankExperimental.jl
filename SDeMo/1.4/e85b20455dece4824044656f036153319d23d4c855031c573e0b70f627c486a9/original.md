```
f1(C::Vector{<:ConfusionMatrix}, full::Bool=false)
```

Version of `f1` using a vector of confusion matrices. Returns the mean, and when the second argument is `true`, returns a tuple where the second argument is the CI.
