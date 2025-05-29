```
solution(pb::Problem;T,x,interpolation)
```

Give the solution of a solved initial-value problem at a given time `T`.

# Arguments

  * Argument `pb` is of type `Problem`.
  * Keyword argument `T` is optional, the last computed time is returned by default.
  * Keyword argument `x` is optional, if provided the solution is interpolated to the collocation vector `x`.
  * Keyword argument `interpolation` is optional, if an integer is provided the solution is interpolated on as many collocation points (if `true`, then the default value `2^3` is chosen).
  * Keyword argument `raw` is optional, if set to `true` then `(U,t)` with `U` the raw data and `t` the time is returned (default is `false`).

# Return values

Return `(η,v,x,t)` where

  * `η` is the surface deformation at collocation points;
  * `v` is the tangential velocity (derivative of the trace of the velocity potential) at collocation points;
  * `x` is the vector of collocation points;
  * `t` the time (first computed time greater or equal to provided `T`).
