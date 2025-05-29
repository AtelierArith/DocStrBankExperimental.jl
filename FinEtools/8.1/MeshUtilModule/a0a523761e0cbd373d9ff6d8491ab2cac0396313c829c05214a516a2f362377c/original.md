```
gradedspace(start::T, stop::T, N::Int)  where {T<:Number}
```

Generate quadratic space.

Generate a quadratic sequence of `N` numbers between `start` and `stop`. This sequence corresponds to separation of adjacent numbers that increases linearly from start to finish.

# Example

```
julia> gradedspace(2.0, 3.0, 5)
5-element Array{Float64,1}:
 2.0
 2.0625
 2.25
 2.5625
 3.0
```
