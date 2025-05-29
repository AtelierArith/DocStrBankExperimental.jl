```julia
struct InitialStepsizeSearch
```

Parameters for the search algorithm for the initial stepsize.

The algorithm finds an initial stepsize $ϵ$ so that the local log acceptance ratio $A(ϵ)$ is near `params.log_threshold`.

  * `initial_ϵ`: The stepsize where the search is started.
  * `log_threshold`: Log of the threshold that needs to be crossed.
  * `maxiter_crossing`: Maximum number of iterations for crossing the threshold.

!!! NOTE

```
The algorithm is from Hoffman and Gelman (2014), default threshold modified to `0.8` following later practice in Stan.
```
