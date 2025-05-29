```
StencilRecurrencePlan{N, D, S, COEF<:NTuple{S,Function}, INIT<:Function} <: AbstractLinearRecurrencePlan
```

# Parameters

  * `N`: system dimension
  * `D`: number domain, e.g. `Real`, `Complex`, etc.
  * `S`: stencil size

# Properties

  * `stencil::SVector{S, CartesianIndex{N}}`: The relative index of the stencil. Can contain `(0,0)` (see `coef`)
  * `coef::COEF<:NTuple{S,Function}`: The coefficient associated with each relative index. The one associated with `CartesianIndex(0,0)` refers to a constant added to that entry. The functions should be in the form `f(T, I...)` where `I` is the index of the stencil and `T` is the suggested return type. Coefficients should be at least as accurate as `T`. Exact-value types such as `Irrational`, `Rational` or `Integer` would do the job, and if that's not possible, `BigFloat` would work as well.
  * `init::INIT<:Function`: the function used for initial values. The functions should be in the form `f(I...)` or `f(T, I...)` where `I` is the size of the array, excluding the last dimension, and `T` is the precisiontype. For the former case, `f` should return exact values, i.e. `Integer`, `Rational` or `Irrational`.
  * `size::Dims{N}`: the size of the whole array.
  * `offset::NTuple{N,Int}`: the very first index where the recurrence starts at.
