```
get_coordinates(M::Segre{𝔽, V}, p, v, ::DefaultOrthonormalBasis; kwargs...)
```

Get coordinates of `X` in the tangent space $T_{(λ, x_1,…, x_d)} \mathcal{S}_A = \mathbb{R} × T_{x_1} \mathbb{S}^{n_1 - 1} ×⋯× T_{x_d} \mathbb{S}^{n_d - 1}$ using a [`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`) on each factor.
