```
promote_to_field(::Type{T})
```

型 `T` をフィールドに昇格させます。たとえば、`promote_to_field(T)` は `T` が整数の場合に `Rational{T}` を返し、`promote_to_field(T)` は `T` が多項式の場合に `RationalPoly{T}` を返します。
