```
shift(f::AbstractGP, a::Real)
shift(f::AbstractGP, a::AbstractVector{<:Real})
```

与えられた `g` は `g(x) = f(x - a)` である DerivedGP を返します。
