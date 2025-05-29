```
nlr(C::Vector{<:ConfusionMatrix}, full::Bool=false)
```

Version of `nlr` using a vector of confusion matrices. Returns the mean, and when the second argument is `true`, returns a tuple where the second argument is the CI.
