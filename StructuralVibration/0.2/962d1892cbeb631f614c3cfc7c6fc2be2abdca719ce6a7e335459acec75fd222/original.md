```
SdofFreeTimeProblem(sdof, u0, t)
```

Structure containing the data of a time problem for a sdof system

**Fields**

  * `sdof::Sdof`: Sdof structure
  * `u0::AbstractVector`: Initial conditions

      * `x0`: Initial displacement [m]
      * `v0`: Initial velocity [m/s]
  * `t::AbstractRange`: Time points at which to evaluate the response
