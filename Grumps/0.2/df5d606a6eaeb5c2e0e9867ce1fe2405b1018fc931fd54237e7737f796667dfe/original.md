```
grumps!( 
    e       :: Estimator,
    d       :: Data{T},
    o       :: OptimizationOptions = OptimizationOptions(),
    θstart  :: StartingVector{T} = nothing,
    seo     :: StandardErrorOptions = StandardErrorOptions();
    printstructure = true
)
```

Conducts the optimization.  You typically just want to set θstart to nothing, i.e. have a starting vector  picked automatically.  
