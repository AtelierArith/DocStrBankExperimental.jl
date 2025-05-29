```
posterior(vfe::VFE, fx::FiniteGP, y::AbstractVector{<:Real})
```

プロセス `f = fx.f` に対する最適な近似事後分布 [1] を計算します。これは、`x` における `f` の観測値 `y` と、誘導点 `vfe.fz.x` に基づいています。

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
