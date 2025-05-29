```
optimizer(x0, params)
```

Generates an optimal trajectory starting from `x0` according to the optimization problem parameterized by `params`. This call is differentaible in `params`.

The output of this function is layed out as `(; xs, us, λs)` with

  * `xs::Vector{<:Vector}`: Vector over time of vector-valued states.
  * `us::Vector{<:Vector}`: Vector over time of vector-valued inputs.
  * `λ::Vector`: Vector of scalar inequlaity-constraint multipliers. By our sign convention, all inequality duals are non-negative.
  * `info::NamedTuple`: Additional "low-level" information. !!Note that this info output field is not differentiable!

# Example

```@example running_example
x0 = zeros(4)
params = zeros(20)
solution = optimizer(x0, params)
```
