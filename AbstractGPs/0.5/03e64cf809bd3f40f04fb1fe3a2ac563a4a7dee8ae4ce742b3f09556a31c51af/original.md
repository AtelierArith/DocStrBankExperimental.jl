```
VFE(fz::FiniteGP)
```

The "Variational Free Energy" sparse approximation [1], used to construct an approximate posterior with inducing inputs `fz.x`. See [`posterior(v::VFE, fx::FiniteGP, y::AbstractVector{<:Real})`](@ref) for a usage example.

[1] - M. K. Titsias. "Variational learning of inducing variables in sparse Gaussian processes". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.
