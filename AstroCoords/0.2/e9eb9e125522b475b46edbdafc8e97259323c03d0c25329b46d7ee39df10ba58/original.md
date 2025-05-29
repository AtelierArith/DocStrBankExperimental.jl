```
angularMomentumVector(u::AbstractVector{<:Number})
```

Computes the instantaneous angular momentum vector from a Cartesian state vector.

# Arguments

-`u::AbstractVector{<:Number}`: The Cartesian state vector [x; y; z; ẋ; ẏ; ż].

# Returns

-'angular_momentum::Vector{<:Number}': 3-Dimensional angular momemtum vector.
