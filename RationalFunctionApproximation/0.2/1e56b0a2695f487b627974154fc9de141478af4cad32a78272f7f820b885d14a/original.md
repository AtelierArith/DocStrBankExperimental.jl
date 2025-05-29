```
DiscretizedPath(path, s::AbstractVector; kwargs...)
DiscretizedPath(path, n::Integer=0; kwargs...)
```

Discretize a path, keeping the option of future making local refinements.

# Arguments

  * `path`: a ComplexCurve or ComplexPath
  * `s`: a vector of parameter values
  * `n`: number of points to discretize the path

# Keyword arguments

  * `refinement`: number of refinements to make between consecutive points
  * `maxpoints`: maximum number of points ever allowed

See also [`collect`](@ref), [`add_node!`](@ref).
