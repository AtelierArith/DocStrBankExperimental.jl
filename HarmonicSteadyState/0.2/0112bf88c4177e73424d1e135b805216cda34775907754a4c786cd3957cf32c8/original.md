```
phase_diagram(res::Result{D}; class="physical", not_class=[]) where {D}
```

Calculate the phase diagram from a `Result` object by summing over the number of states at each swept parameters.

# Keyword arguments

Class selection done by passing `String` or `Vector{String}` as kwarg:

```
class::String       :   only count solutions in this class ("all" --> plot everything)
not_class::String   :   do not count solutions in this class
```

# Returns

  * Array{Int64,D}: Sum of states after applying the specified class masks
