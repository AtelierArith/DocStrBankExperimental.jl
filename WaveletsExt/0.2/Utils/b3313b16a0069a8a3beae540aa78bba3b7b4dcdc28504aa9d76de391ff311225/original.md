```
duplicatesignals(x, n, k[, noise=false, t=1])
```

Given a signal `x`, returns `n` shifted versions of the signal, each with shifts of multiples of `k`. 

Setting `noise = true` allows randomly generated Gaussian noises of μ = 0,  σ² = t to be added to the circularly shifted signals.

# Arguments

  * `x::AbstractVector{T} where T<:Number`: 1D-signal to be duplicated.
  * `n::Integer`:: Number of duplicated signals.
  * `k::Integer`:: Circular shift size for each duplicated signal.
  * `noise::Bool`: (Default: `false`) Whether or not to add Gaussian noise.
  * `t::Real`: (Default: 1) Relative size of noise.

# Returns

`::Array{T}`: Duplicated signals.

# Examples

```@repl
using WaveletsExt

x = generatesignals(:blocks)
duplicatesignals(x, 5, 0)      # [x x x x x]
```

*See also:* [`generatesignals`](@ref)
