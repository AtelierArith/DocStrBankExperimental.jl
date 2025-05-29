Hidden Markov model parameters.

# Fields

```
penalty::Float64: penalty on hidden Markov model. Defualt = 200.
minimumFrequency::Int64: minimun frequency on model state to split during hypothesis generation. Default = 20.
verbosity::Bool: increase verbosity. Default = false.
distance::Function: calculate distance. Possible options provided by this package inlcude: `euclDist`, `bhattDist`. Alternatively, a predefined or an anonymous / λ functions with the form `functionDist(arr::Array{T, 1}, h::Array{T, 1}) where T <: Number` can be passed.
```

See also: [`HMM`](@ref), [`setup`](@ref), [`euclDist`](@ref), [`bhattDist`](@ref),
