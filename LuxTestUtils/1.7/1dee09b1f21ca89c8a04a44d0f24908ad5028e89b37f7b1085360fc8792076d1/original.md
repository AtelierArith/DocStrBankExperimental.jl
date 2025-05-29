```
test_gradients(f, args...; skip_backends=[], broken_backends=[], kwargs...)
```

Test the gradients of `f` with respect to `args` using the specified backends.

| Backend        | ADType              | CPU | GPU | Notes             |
|:-------------- |:------------------- |:--- |:--- |:----------------- |
| Zygote.jl      | `AutoZygote()`      | ✔   | ✔   |                   |
| Tracker.jl     | `AutoTracker()`     | ✔   | ✔   |                   |
| ReverseDiff.jl | `AutoReverseDiff()` | ✔   | ✖   |                   |
| ForwardDiff.jl | `AutoForwardDiff()` | ✔   | ✖   | `len ≤ 100`       |
| FiniteDiff.jl  | `AutoFiniteDiff()`  | ✔   | ✖   | `len ≤ 100`       |
| Enzyme.jl      | `AutoEnzyme()`      | ✔   | ✖   | Only Reverse Mode |

## Arguments

  * `f`: The function to test the gradients of.
  * `args`: The arguments to test the gradients of. Only `AbstractArray`s are considered for gradient computation. Gradients wrt all other arguments are assumed to be `NoTangent()`.

## Keyword Arguments

  * `skip_backends`: A list of backends to skip.
  * `broken_backends`: A list of backends to treat as broken.
  * `soft_fail`: If `true`, then the test will be recorded as a `soft_fail` test. This overrides any `broken` kwargs. Alternatively, a list of backends can be passed to `soft_fail` to allow soft_fail tests for only those backends.
  * `enzyme_set_runtime_activity`: If `true`, then activate runtime activity for Enzyme.
  * `enable_enzyme_reverse_mode`: If `true`, then enable reverse mode for Enzyme.
  * `kwargs`: Additional keyword arguments to pass to `check_approx`.

## Example

```julia
julia> f(x, y, z) = x .+ sum(abs2, y.t) + sum(y.x.z)

julia> x = (; t=rand(10), x=(z=[2.0],))

julia> test_gradients(f, 1.0, x, nothing)

```
