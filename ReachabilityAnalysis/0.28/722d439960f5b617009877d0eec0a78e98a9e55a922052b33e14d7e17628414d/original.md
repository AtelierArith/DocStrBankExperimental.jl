```
GLGM06{N, AM, S, D, NG, P, RM} <: AbstractContinuousPost
```

Implementation of the Girard–Le Guernic–Maler algorithm for reachability of linear systems using zonotopes.

## Fields

  * `δ`                – step-size of the discretization
  * `approx_model`     – (optional, default: `FirstOrderZonotope()`) approximation                       model; see `Notes` below for possible options
  * `max_order`        – (optional, default: `5`) maximum zonotope order
  * `static`           – (optional, default: `false`) if `true`, convert the problem data                       to statically sized arrays
  * `dim`              – (optional default: `missing`) ambient dimension
  * `ngens`            – (optional, default: `missing`) number of generators
  * `preallocate`      – (optional, default: `true`) if `true`, use the implementation                       which preallocates the zonotopes prior to applying the update rule
  * `reduction_method`    – (optional, default: `GIR05()`) zonotope order reduction method used
  * `disjointness_method` – (optional, default: `NoEnclosure()`) method to check                          disjointness between the reach-set and the invariant

## Notes

The type parameters are:

  * `N`  – number type of the step-size
  * `AM` – approximation model
  * `S`  – value type of the `static` option
  * `D`  – value type of the dimension of the system `dim`
  * `NG` – value type of the number of generators `ngens`
  * `P`  – value type of the `preallocate` option
  * `RM` – type of the reduction method

The only parameter that does not have a default value is the step size `δ`, associated with the type parameter `N`. Parameters `dim` and `ngens` are optionally specified (default to `missing`). These parameters are needed for the cases that require the size of the zonotopes to be known (fixed) at compile time, namely the `static=true` version of this algorithm.

The default approximation model is [`FirstOrderZonotope`](@ref).

## References

The main ideas behind this algorithm can be found in [Girard05](@citet) and [GirardGM06](@citet). These methods are discussed at length in the dissertation [LeGuernicG09](@cite).

Regarding the zonotope order reduction methods, we refer to [Combastel03, Girard05](@citet) and the review article [YangS18](@cite).
