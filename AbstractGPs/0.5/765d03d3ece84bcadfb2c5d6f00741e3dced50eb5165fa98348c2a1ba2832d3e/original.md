```
posterior(vfe::VFE, fx::FiniteGP, y::AbstractVector{<:Real})
```

Compute the optimal approximate posterior [1] over the process `f = fx.f`, given observations `y` of `f` at `x`, and inducing points `vfe.fz.x`.

```jldoctest
julia> f = GP(Matern52Kernel());

julia> x = randn(1000);

julia> z = range(-5.0, 5.0; length=13);

julia> vfe = VFE(f(z));

julia> y = rand(f(x, 0.1));

julia> post = posterior(vfe, f(x, 0.1), y);

julia> post(z) isa AbstractGPs.FiniteGP
true
```

[1] - M. K. Titsias. "Variational learning of inducing variables in sparse Gaussian processes". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.
