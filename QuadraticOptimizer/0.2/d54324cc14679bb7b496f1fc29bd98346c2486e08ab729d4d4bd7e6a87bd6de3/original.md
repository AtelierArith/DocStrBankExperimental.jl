```
optimize_qim(f, ps_init::Vector{<:SVector{D, <:Real}}, fs_init::Vector{<:Real}, n_iter::Integer) -> ps, fs
```

Optimize a function `f` using the Quadratic Interpolation Method (QIM).

# Arguments

  * `f`: The objective function to be optimized.
  * `ps_init`: A vector of points in $\mathbb{R}^D$ where `f` has been evaluated.
  * `fs_init`: A vector of function values corresponding to the points in `ps_init`.
  * `n_iter`: The number of optimizing iterations. After execution, the length of `ps` will be `N + n_iter`, where `N = length(ps)` before execution.

!!! note
    In each step of the QIM, the last `M` (`==((D+2)*(D+1)/2)`) points from `ps` and `fs` are used to interpolate with a quadratic function. The method iteratively refines the points and function values, extending `ps` and `fs` with `n_iter` additional points resulting from the optimization process.


# Examples

```jldoctest
julia> using QuadraticOptimizer, StaticArrays, Random

julia> Random.seed!(42);

julia> f(p) = p[1]^2 + sin(p[1]) + 1.5p[2]^2 + sinh(p[2]) - p[1]*p[2]/5
f (generic function with 1 method)

julia> ps_init = [@SVector rand(2) for _ in 1:6]
6-element Vector{SVector{2, Float64}}:
 [0.6293451231426089, 0.4503389405961936]
 [0.47740714343281776, 0.7031298490032014]
 [0.6733461456394962, 0.16589443479313404]
 [0.6134782250008441, 0.6683403279577278]
 [0.4570310908017041, 0.2993652953937611]
 [0.6611433726193705, 0.6394313620423493]

julia> ps, fs = optimize_qim(f, ps_init, f.(ps_init), 20);
```
