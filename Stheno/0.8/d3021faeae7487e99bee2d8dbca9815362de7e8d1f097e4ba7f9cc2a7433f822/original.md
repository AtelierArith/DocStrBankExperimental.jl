```
shift(f::AbstractGP, a::Real)
shift(f::AbstractGP, a::AbstractVector{<:Real})
```

Returns the DerivedGP `g` given by `g(x) = f(x - a)`
