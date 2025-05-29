```
optimize_qim(f, xs_init::Vector{<:Real}, n_iter::Integer) -> xs, fs
```

Optimize a function `f` using the Quadratic Interpolation Method (QIM).

# Arguments

  * `f`: The objective function to be optimized.
  * `xs_init`: A vector of points in $\mathbb{R}^D$ where `f` has been evaluated.
  * `n_iter`: The number of optimizing iterations. After execution, the length of `xs` will be `N + n_iter`, where `N = length(xs)` before execution.

!!! note
    In each step of the QIM, the last `3` points from `xs` and `fs` are used to interpolate with a quadratic function. The method iteratively refines the points and function values, extending `xs` and `fs` with `n_iter` additional points resulting from the optimization process.


# Examples

```jldoctest
julia> using QuadraticOptimizer

julia> f(x) = sin(x) + x^2/10  # Function to minimize
f (generic function with 1 method)

julia> xs_init = [1.2, 0.1, -2.2]  # Initial points (3 points are required to construct parabola)
3-element Vector{Float64}:
  1.2
  0.1
 -2.2

julia> xs = copy(xs_init)  # Keep initial points
3-element Vector{Float64}:
  1.2
  0.1
 -2.2

julia> xs, fs = optimize_qim(f, xs, 10);  # Optimize 10 steps
```
