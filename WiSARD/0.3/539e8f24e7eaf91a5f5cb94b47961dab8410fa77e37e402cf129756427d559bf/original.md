```
classify(wnn::WNN, y::Vector{Bool}; bleach=0::Int, gamma=0.5::Float)
```

Classifies input `y` returning some label `x`. If no training happened, `nothing` will be returned instead.
