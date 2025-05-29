```
KeplerSolver(M::T, e::Number; tol::Float64=10 * eps(T)) where {T<:Number}
```

Solves for true anomaly given the mean anomaly and eccentricity of an orbit.

# Arguments

-`M::Number`: Mean Anomaly of the orbit [radians]. -`e::Number`: Eccentricity of the orbit.

# Keyword Arguments

-`tol::Float64`: Convergence tolerance of Kepler solver. [Default=10*eps(T)]

# Returns

-`f::Number``: True Anomaly of the orbit [radians]
