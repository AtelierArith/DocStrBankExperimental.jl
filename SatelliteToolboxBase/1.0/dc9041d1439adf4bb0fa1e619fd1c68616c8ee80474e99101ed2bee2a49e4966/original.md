```
mean_to_eccentric_anomaly(e::T1, M::T2; max_iterations::Integer = 10, tol::Union{Nothing, Number} = nothing) where {T1, T2} -> T
```

Compute the eccentric anomaly (0, 2π) [rad] given the orbit eccentricity `e` and the mean anomaly `M` [rad].

This function uses the Newton-Raphson algorithm to solve the Kepler's equation.

!!! note
    The output type `T` is obtained by promoting `T1` and `T2` to float.


# Keywords

  * `tol::Union{Nothing, Number}`: Tolerance to accept the solution from Newton-Raphson   algorithm. If `tol` is `nothing`, it will be `eps(T)`.   (**Default** = `nothing`)
  * `max_iterations::Number`: Maximum number of iterations allowed for the Newton-Raphson   algorithm. If it is lower than 1, then it is set to 10.   (**Default** = 10)
