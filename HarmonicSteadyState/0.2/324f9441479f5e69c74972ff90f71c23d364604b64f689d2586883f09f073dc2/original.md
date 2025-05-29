```
attractors(res::Result{D}; class="stable", not_class=[]) where D
```

Extract attractors from a [`Result`](@ref) object. Returns an array of dictionaries, where each dictionary maps branch identifier to the attractor. The attractors are filtered by their corresponding class.

# Keyword arguments

Class selection done by passing `String` or `Vector{String}` as kwarg:

```
class::String       :   only count solutions in this class ("all" --> plot everything)
not_class::String   :   do not count solutions in this class
```

# Returns

`Array{Dict,D}`: Vector of dictionaries mapping branch indices to points satisfying   the stability criteria at each parameter value
