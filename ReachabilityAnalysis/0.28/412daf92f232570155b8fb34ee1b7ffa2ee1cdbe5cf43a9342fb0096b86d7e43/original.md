```
ASB07{N, AM, RM, S, R} <: AbstractContinuousPost
```

Implementation of Althoff - Stursberg - Buss algorithm for reachability of linear systems with uncertain parameters and inputs using zonotopes.

## Fields

  * `δ`                – step-size of the discretization
  * `approx_model`     – (optional, default: `CorrectionHull(; order=10, exp=:interval)`)                       approximation model;                       see `Notes` below for possible options
  * `max_order`        – (optional, default: `5`) maximum zonotope order
  * `reduction_method` – (optional, default: `GIR05()`) zonotope order reduction method used
  * `static`           – (optional, default: `false`) if `true`, convert the problem data                       to statically sized arrays
  * `recursive`        – (optional default: `true`) if `true`, use the implementation that                       recursively computes each reach-set; otherwise, use the implementation                       that unwraps the sequence until the initial set

## Notes

The type fields are:

  * `N`  – number type of the step-size
  * `AM` – type of the approximation model
  * `RM` – type associated to the reduction method
  * `S`  – value type associated to the `static` option
  * `R`  – value type associated to the `recursive` option

The sole parameter which doesn't have a default value is the step-size, associated to the type parameter `N`.

The default approximation model is

```julia
approx_model=CorrectionHull(order=10, exp=:base)
```

Here, `CorrectionHull` refers to an implementation of the interval matrix approximation method described in [AlthoffSB07](@citet). For technicalities on interval matrix operations, we refer to the package `IntervalMatrices.jl`.

## References

The main ideas behind this algorithm can be found in [AlthoffSB07](@citet). These methods are discussed at length in the dissertation [Althoff10](@cite).

Regarding the zonotope order reduction methods, we refer to [Combastel03, Girard05](@citet) and the review article [YangS18](@cite).
