```julia
Gθ(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Any, Bool}

```

Returns the antiderivative $G_\theta=\int\frac{d\theta}{\sqrt{\Theta(\theta)}}$. See [`θ_potential(x)`](@ref) for an implementation of $\Theta(	heta)$.

# Arguments

  * `pix` : Pixel information
  * `θs` : Emission inclination
  * `isindir` : Is the path direct or indirect?
  * `n` : nth image ordered by minotime
