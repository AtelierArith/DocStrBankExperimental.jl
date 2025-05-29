```
overapproximate(X::LazySet, ZT::Type{<:Zonotope},
                dir::Union{AbstractDirections, Type{<:AbstractDirections}};
                [algorithm]="vrep", kwargs...)
```

Overapproximate a set with a zonotope.

### Input

  * `X`         – set
  * `Zonotope`  – target set type
  * `dir`       – directions used for the generators
  * `algorithm` – (optional, default: `"vrep"`) algorithm used to compute the                overapproximation
  * `kwargs`    – further algorithm-specific options

### Output

A zonotope that overapproximates `X` and uses at most the generator directions provided in `dir` (redundant directions will be ignored).

### Notes

Two algorithms are available:

  * `"vrep"` – Overapproximate a polytopic set with a zonotope of minimal total generator sum using only generators in the given directions. Under this constraint, the zonotope has the minimal sum of generator vectors. See the docstring of [`_overapproximate_zonotope_vrep`](@ref) for further details.
  * `"cpa"` – Overapproximate a polytopic set with a zonotope using a Cartesian decomposition into two-dimensional blocks. See the docstring of [`_overapproximate_zonotope_cpa`](@ref) for further details.
