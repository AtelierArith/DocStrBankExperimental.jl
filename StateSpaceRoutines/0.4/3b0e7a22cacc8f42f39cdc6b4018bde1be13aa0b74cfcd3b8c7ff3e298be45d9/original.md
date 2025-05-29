```
function chand_recursion(y::Matrix{S}, T::Matrix{S}, R::Matrix{S}, C::Vector{S},
                         Q::Matrix{S}, Z::Matrix{S}, D::Vector{S}, H::Matrix{S},
                         s_pred::Vector{S} = Vector{S}(0),
                         P_pred::Matrix{S} = Matrix{S}(0,0);
                         allout::Bool = false, Nt0::Int = 0,
                         tol::Float64 = 0.0) where {S<:AbstractFloat}
```

Implementation of Chandrasekhar Recursions, a faster algorithm for likelihood evaluation in a linear Gaussian state space system. Based on code by Ed Herbst.

State Transition equation:

```
s_t = TT * s_{t-1} + RR * ε_t, ε_t ~ iid N(0, QQ)
```

Measurement equation:

```
y_t = DD + ZZ * s_t + η_t, η_t ~ iid N(0, HH)
```

Returns log-likelihood evaluation.
