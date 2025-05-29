```
scale(λ::Int,Ω::UnitRange{Int})
```

Range scaling.

**Caveat:**

We do not use Julia `*` operator as it returns a step range:

```jldoctest
julia> r=6:8
6:8

julia> -2*r
-12:-2:-16
```

What we need is:

```jldoctest
julia> r=6:8
6:8

julia> scale(-2,r)
-16:-12
```
