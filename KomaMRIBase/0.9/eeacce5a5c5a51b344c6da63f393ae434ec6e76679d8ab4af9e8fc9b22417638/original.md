```
spinrange = SpinRange(range)
```

SpinRange struct. It is a specialized type that inherits from AbstractSpinSpan and is used to select a certain range and number of spins.

# Arguments

  * `range`: (`::AbstractVector`) spin id's. This argument can be a Range, a Vector or a BitVector

# Returns

  * `spinrange`: (`::SpinRange`) SpinRange struct

# Examples

```julia-repl
julia> spinrange = SpinRange(1:10)
julia> spinrange = SpinRange([1, 3, 5, 7])
julia> spinrange = SpinRange(obj.x .> 0)
```
