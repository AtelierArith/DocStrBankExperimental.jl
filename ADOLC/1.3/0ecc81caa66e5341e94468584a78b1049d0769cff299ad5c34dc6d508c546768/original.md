```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    mode::Symbol;
    dir::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    weights::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

A variant of the [`derivative`](@ref) driver, which can be used to compute [first-order](@ref "First-Order") and [second-order](@ref "Second-Order")  derivatives, as well as the [abs-normal-form](@ref "Abs-Normal-Form")  of the given function `f` at the point `x`. The available modes are listed [here](@ref "Derivative Modes"). The formulas in the tables define `weights` (left multiplier) and `dir` (right multiplier). Most modes leverage a tape, which has the identifier `tape_id`. If there is already a valid  tape for the function `f` at the selected point `x` use `reuse_tape=true` and set the `tape_id` accordingly to avoid the re-creation of the tape.

# Examples:

First-Order:

```jldoctest
f(x) = sin(x)
res = derivative(f, float(π), :jac)

# output

1-element CxxVector:
 -1.0
```

Second-Order:

```jldoctest
f(x) = [x[1]*x[2]^2, x[1]^2*x[3]^3]
x = [1.0, 2.0, -1.0]
dir = [1.0, 0.0, 0.0]
weights = [1.0, 1.0]
res = derivative(f, x, :vec_hess_vec, dir=dir, weights=weights)

# output

3-element CxxVector:
 -2.0
  4.0
  6.0
```

Abs-Normal-Form:

```jldoctest
f(x) = max(x[1]*x[2], x[1]^2)
x = [1.0, 1.0]
res = derivative(f, x, :abs_normal)

# output

AbsNormalForm(0, 1, 2, 1, [1.0, 1.0], [1.0], [0.0], [0.0], [1.0], [1.5 0.5], [0.5;;], [1.0 -1.0], [0.0;;])
```
