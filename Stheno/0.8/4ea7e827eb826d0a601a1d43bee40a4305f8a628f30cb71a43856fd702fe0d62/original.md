```
SparseFiniteGP{T1<:FiniteGP, T2<:FiniteGP}
```

A finite-dimensional projection of an `AbstractGP` `f` at locations `x`, which uses a second `FiniteGP` defined at a sparse set of inducing points [1] to do approximate inference.

This object has similar methods to an ordinary `FiniteGP`, but when you call `logpdf` on it, it actually computes the `elbo`, and when you call `posterior` on it, you get an approximate posterior.

[1] - M. K. Titsias. "Variational learning of inducing variables in sparse Gaussian processes". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.

```jldoctest
julia> f = atomic(GP(Matern32Kernel()), GPC());

julia> fobs = f(rand(100));

julia> finducing = f(0:0.1:1);

julia> fxu = SparseFiniteGP(fobs, finducing);

julia> y = rand(fxu);

julia> logpdf(fxu, y) < logpdf(fobs, y)
true
```
