```julia
integrate(, coordl, coordr, hnormal, velofunc; kwargs...)

```

This is an internal function to integrate `velofunc` along the edge $\sigma=\overline{\mathtt{coordl}\,\mathtt{coordr}}$ between the $x_K$ and $x_L$ where $\mathtt{hnormal}=x_K-x_L$ using [Simpson's Rule](https://en.wikipedia.org/wiki/Simpson%27s_rule). To be precise, compute for a cartesian coordinate system: $\int_{\sigma} \mathbf{v} \cdot \mathbf{n} \,\mathrm{ds} \lvert x_K - x_L \rvert / \lvert\sigma\rvert$.
