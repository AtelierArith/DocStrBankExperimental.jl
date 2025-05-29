```
LGG09{N, AM, TN<:AbstractDirections} <: AbstractContinuousPost
```

Implementation of Girard - Le Guernic algorithm for reachability analysis using support functions.

## Fields

  * `δ`            – step-size of the discretization
  * `approx_model` – (optional, default: `Forward`) approximation model;                   see `Notes` below for possible options
  * `template`     – (alias: `dirs`) struct that holds the directions (either lazily or concretely)                   for each support function evaluation defining the template
  * `static`       – (optional, default: `false`) if `true`, use statically sized arrays
  * `threaded`     – (optional, default: `false`) if `true`, use multi-threading                   to compute different template directions in parallel
  * `sparse`       – (optional, default: `false`) if `true`, convert the matrix exponential                   obtained after discretization to a sparse matrix
  * `cache`        – (optional, default: `true`) if `true`, use a cache for intermediate                   computations in the set recurrence loop
  * `vars`         – (optional, default: `missing`) an integer or a vector of integers                   specifying the variables of interest to automatically construct a template                   using canonical directions; requires that `n` (or `dim`) is specified as well

## Notes

The type fields are:

  * `N`        – number type of the step-size
  * `AM`       – type of the approximation model
  * `TN`       – type of the abstract directions that define the template

The flag `threaded=true` specifies that the support functions along different directions should be computed in parallel. See the section on [Multi-threading](@ref) for details on how to setup the number of threads.

## References

This is an implementation of the algorithm from [LeGuernicG09](@citet).

These methods are described at length in the dissertation [LeGuernicG09](@cite).
