```
marginals(f::FiniteGP)
```

Compute a vector of Normal distributions representing the marginals of `f` efficiently. In particular, the off-diagonal elements of `cov(f(x))` are never computed.

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> fs = marginals(f(x));

julia> mean.(fs) == mean(f(x))
true

julia> std.(fs) == sqrt.(diag(cov(f(x))))
true
```
