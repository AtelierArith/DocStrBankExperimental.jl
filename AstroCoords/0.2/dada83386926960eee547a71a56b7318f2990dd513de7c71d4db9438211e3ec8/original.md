```
meanAnomaly2TrueAnomaly(M::T, e::Number; tol::Float64=10 * eps(T)) where {T<:Number}
```

Converts the mean anomaly into the true anomaly.

# Arguments

-`M::Number`: Mean anomaly of the orbit [radians]. -`e::Number`: Eccentricity of the orbit.

# Keyword Arguments

-`tol::Float64`: Convergence tolerance of Kepler solver. [Default=10*eps(T)]

# Returns

-`f::Number`: Mean anomaly of the orbit [radians].
