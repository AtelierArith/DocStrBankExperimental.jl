```
angularMomentumVector(X::AstroCoord, μ::Number)
```

Computes the instantaneous angular momentum vector from a Cartesian state vector.

# Arguments

-`X::AstroCoord`: An coordinate set describing the orbit. -`μ::Number`: Standard graviational parameter of central body.

# Returns

-`angular_momentum::Vector{<:Number}`: 3-Dimensional angular momemtum vector.
