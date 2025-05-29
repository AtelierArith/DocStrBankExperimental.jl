```
struct StringMonoid <: Monoid
    val::AbstractString
end
```

String monoid: $R = (\Sigma\^*, concat, \epsilon)$.
