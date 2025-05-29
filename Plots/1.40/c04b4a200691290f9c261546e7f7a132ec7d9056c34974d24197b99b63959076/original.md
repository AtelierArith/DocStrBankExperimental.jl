```
density(x)
density!(x)
```

Make a line plot of a kernel density estimate of x. The smoothness of the density plot is defined from `bandwidth` (real positive number).

# Arguments

  * `x`: AbstractVector of samples for probability density estimation

# Keyword arguments

  * `trim`::Bool: enables cutting off the distribution tails.
  * `bandwidth`::Number: a low bandwidth induces under-smoothing, whilst a high bandwidth induces over-smoothing.

# Examples

```julia-repl
julia> density(randn(100), bandwidth = -0.01, trim = false)
output : ERROR: Bandwidth must be positive

julia> density(randn(100), bandwidth = 0.1, trim = false)  # a curve with extremity and under-smoothing
julia> density(randn(100), bandwidth = 10, trim = true)  # a curve without extremity and over-smoothing
```

# Example

```julia-repl
julia> using StatsPlots
julia> density(randn(100_000))
```
