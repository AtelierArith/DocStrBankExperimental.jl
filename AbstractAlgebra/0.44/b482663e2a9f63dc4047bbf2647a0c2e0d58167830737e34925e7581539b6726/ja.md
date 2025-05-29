```
identity_map(R::D) where D <: AbstractAlgebra.Set
```

ドメイン $R$ に対する恒等写像を返します。

# 例

```jldoctest
julia> R, t = ZZ[:t]
(Univariate polynomial ring in t over integers, t)

julia> f = identity_map(R)
Identity map
  of univariate polynomial ring in t over integers

julia> f(t)
t
```
