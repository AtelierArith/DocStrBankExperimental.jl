```
ForcingModelAndRegion
```

A type that holds the forcing model function, region, and cache

# Constructors

`ForcingModelAndRegion(model::AbstractForcingModel,cache::BasicILMCache)`

`ForcingModelAndRegion(modellist::Vector{AbstractForcingModel},cache::BasicILMCache)`

These forms generally get called when building the extra cache. They also gracefully generate an empty list of models if one passes along `nothing` in the first argument.
