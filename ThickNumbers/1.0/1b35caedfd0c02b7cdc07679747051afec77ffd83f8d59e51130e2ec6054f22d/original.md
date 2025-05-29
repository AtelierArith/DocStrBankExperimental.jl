```
lohi(::Type{TN}, lo, hi) where TN<:ThickNumber
```

Construct a `TN` from its `lo` and `hi` values.

# Interface requirements

`lohi` must be implemented by all ThickNumber subtypes.

If

```julia
x = lohi(TN, lo, hi)
```

succeeds without throwing an error, then it is required that

```julia
typeof(x) <: TN
lo ∈ x
hi ∈ x
lo ≈ loval(x)
hi ≈ hival(x)
```

For the latter two, exact equality is not required; this allows for roundoff error (in case `TN` is parametrized by something other than its `lo` and `hi` values) as well as outward rounding for ThickNumber types that aim to be conservative and guarantee acccuracy even in the presence of roundoff error.
