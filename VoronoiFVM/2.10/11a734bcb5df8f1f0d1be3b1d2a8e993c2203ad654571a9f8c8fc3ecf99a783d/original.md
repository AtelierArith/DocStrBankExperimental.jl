```julia
integrate(, coordl, coordr, hnormal, velofunc; kwargs...)

```

This is an internal function similar to `integrate(::Type{<:Cartesian2D},...)`, but computes instead $\int_{\sigma} r \, \mathbf{v} \cdot \mathbf{n} \,\mathrm{ds} \lvert x_K - x_L \rvert / \left ( \lvert\sigma\rvert r(\mathrm{mid}(\sigma)) \right )$ where $r(\mathrm{mid}(\sigma))$ is the $r$-coordinate of the mid-point of $\sigma$.
