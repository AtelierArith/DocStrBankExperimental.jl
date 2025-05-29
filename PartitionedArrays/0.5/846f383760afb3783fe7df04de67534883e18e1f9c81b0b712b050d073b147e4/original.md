```
PTimer(ranks;verbose::Bool=false)
```

Construct an instance of [`PTimer`](@ref) by using the same data distribution as for `ranks`.  If `verbose==true`, then a message will be printed each time a new section is added in the timer when calling [`toc!`](@ref).
