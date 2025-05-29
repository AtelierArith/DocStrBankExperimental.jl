```
struct StringMonoid <: Monoid
    val::AbstractString
end
```

文字列モノイド: $R = (\Sigma\^*, concat, \epsilon)$。
