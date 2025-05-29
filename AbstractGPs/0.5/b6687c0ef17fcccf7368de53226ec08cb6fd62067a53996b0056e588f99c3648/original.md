```
approx_log_evidence(vfe::VFE, fx::FiniteGP, y::AbstractVector{<:Real})
elbo(vfe::VFE, fx::FiniteGP, y::AbstractVector{<:Real})
```

The Titsias Evidence Lower BOund (ELBO) [1]. `y` are observations of `fx`, and `v.z` are inducing points.

```jldoctest
julia> f = GP(Matern52Kernel());

julia> x = randn(1000);

julia> z = range(-5.0, 5.0; length=13);

julia> v = VFE(f(z));

julia> y = rand(f(x, 0.1));

julia> elbo(v, f(x, 0.1), y) < logpdf(f(x, 0.1), y)
true
```

[1] - M. K. Titsias. "Variational learning of inducing variables in sparse Gaussian processes". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.
