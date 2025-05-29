```
mean(fx::FiniteGP)
```

Compute the mean vector of `fx`.

```jldoctest
julia> f = GP(Matern52Kernel());

julia> x = randn(11);

julia> mean(f(x)) == zeros(11)
true
```
