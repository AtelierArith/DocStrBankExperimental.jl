```
LogNormalOnset <: AbstractOnset
```

Log-normal inter-event distances (in samples) using the `Distributions.jl` truncated LogNormal distribution ([code and mathematical reference](https://juliastats.org/Distributions.jl/stable/univariate/#Distributions.LogNormal)).

Be careful with large `μ` and `σ` values, as they are on logscale. σ>8 can quickly give you out-of-memory sized signals! 
Tip: To manually generate inter-event distance samples use the [`simulate_interonset_distances`](@ref) function.

# Fields

  * `μ`: The mean of the log-transformed variable (the log-normal random variable's logarithm follows a normal distribution).
  * `σ`: The standard deviation of the log-transformed variable.
  * `offset = 0` (optional): The minimal distance between events.
  * `truncate_upper = nothing` (optional): Upper limit (in samples) at which the distribution is truncated.

# Examples

```julia-repl
julia> onset_distribution = LogNormalOnset(3, 0.25, 10, 25)
LogNormalOnset
  μ: Int64 3
  σ: Float64 0.25
  offset: Int64 10
  truncate_upper: Int64 25
```

See also [`UniformOnset`](@ref), [`NoOnset`](@ref).
