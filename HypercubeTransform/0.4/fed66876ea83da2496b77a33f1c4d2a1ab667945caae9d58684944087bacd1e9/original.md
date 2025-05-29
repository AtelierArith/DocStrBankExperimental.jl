```
NamedDist(d::NamedTuple{N})
NamedDist(;dists...)
```

A Distribution with names `N`. This is useful to construct a set of random variables with a set of names attached to them.

```julia-repl
julia> d = NamedDist((a=Normal(), b = Uniform(), c = MvNormal(randn(2), rand(2))))
julia> x = rand(d)
(a = 0.13789342, b = 0.2347895, c = [2.023984392, -3.09023840923])
julia> logpdf(d, x)
```

Note that NamedDist values passed to NamedDist can also be abstract collections of distributions as well

```julia-repl
julia> d = NamedDist(a = Normal(),
                     b = MvNormal(ones(2)),
                     c = (Uniform(), InverseGamma())
                     d = (a = Normal(), Beta)
                    )
```

How this is done internally is considered an implementation detail and is not part of the public interface.
