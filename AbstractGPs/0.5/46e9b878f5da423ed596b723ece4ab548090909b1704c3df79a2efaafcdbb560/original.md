```
posterior(fx::FiniteGP, y::AbstractVector{<:Real})
posterior(approx::<Approximation>, fx::FiniteGP, y::AbstractVector{<:Real})
posterior(approx::<Approximation>, lfx::LatentFiniteGP, y::AbstractVector)
```

Construct the posterior distribution over the latent Gaussian process (`fx.f` or `lfx.fx.f`), given the observations `y` corresponding to the process's finite projection (`fx` or `lfx`).

In the two-argument form, this describes exact GP regression with `y` observed under a Gaussian likelihood, and returns a `PosteriorGP`.

In the three-argument form, the first argument specifies the approximation to be used (e.g. `VFE` or defined in other packages such as ApproximateGPs.jl), and returns an `ApproxPosteriorGP`.
