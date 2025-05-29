```
identity_map(R::D) where D <: AbstractAlgebra.Set
```

Return an identity map on the domain $R$.

# Examples

```jldoctest
julia> R, t = ZZ[:t]
(Univariate polynomial ring in t over integers, t)

julia> f = identity_map(R)
Identity map
  of univariate polynomial ring in t over integers

julia> f(t)
t
```
