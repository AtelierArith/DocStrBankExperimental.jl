```
meanAnomaly2EccentricAnomaly(M::T, e::Number; tol::Float64=10 * eps(T)) where {T<:Number}
```

Converts the Mean Anomaly into the Eccentric Anomaly

# Arguments

-`M::Number`: Mean Anomaly of the orbit [radians] -`e::Number`: Eccentricity of the orbit

# Keyword Arguments

-`tol::Float64`: Convergence tolerance of Kepler solver. [Default=10*eps(T)]

# Returns

-`E::Number`: Eccentric Anomaly of the orbit [radians]
