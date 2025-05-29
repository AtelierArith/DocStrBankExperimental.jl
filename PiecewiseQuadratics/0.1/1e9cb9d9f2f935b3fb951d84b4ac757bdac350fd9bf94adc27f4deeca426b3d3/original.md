```
get_plot(f::PiecewiseQuadratic; N::Int64=1000)
```

Return `x`, `y` `N`-vectors for use with plotting libraries.

# Example

```julia
julia> using Plots

julia> f = PiecewiseQuadratic([
         BoundedQuadratic(-Inf, 3.0, 1.0, -3.0, 3.0),
         BoundedQuadratic(3.0, 4.0, 0.0, -1.0, 3.0),
         BoundedQuadratic(4.0, 6.0, 2.0, -20.0, 47.0),
         BoundedQuadratic(6.0, 7.5, 0.0, 1.0, -7.0),
         BoundedQuadratic(7.5, Inf, 0.0, 4.0, -29.0)
       ])
Piecewise quadratic function:
BoundedQuadratic: f(x) = 1.00000 x² - 3.00000 x + 3.00000, ∀x ∈ [-Inf, 3.00000]
BoundedQuadratic: f(x) = - 1.00000 x + 3.00000, ∀x ∈ [3.00000, 4.00000]
BoundedQuadratic: f(x) = 2.00000 x² - 20.00000 x + 47.00000, ∀x ∈ [4.00000, 6.00000]
BoundedQuadratic: f(x) = + 1.00000 x - 7.00000, ∀x ∈ [6.00000, 7.50000]
BoundedQuadratic: f(x) = + 4.00000 x - 29.00000, ∀x ∈ [7.50000, Inf]

julia> plot(get_plot(f); grid=false, linestyle=:dash, color=:black, label="piece-wise quadratic")
Plot{Plots.GRBackend() n=1}

julia> plot!(get_plot(simplify(envelope(f))); color=:blue, la=0.5, label="envelope")
Plot{Plots.GRBackend() n=2}

```
