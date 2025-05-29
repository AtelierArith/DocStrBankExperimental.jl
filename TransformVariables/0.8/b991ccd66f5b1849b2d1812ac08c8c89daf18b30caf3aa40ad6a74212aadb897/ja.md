```
inverse(t, y)
```

`transform(t, x) ≈ y` となる `x` を返します。

```
inverse(t)
```

`y -> inverse(t, y)` に相当する呼び出し可能なものを返します。`t` は `transform` で作成された呼び出し可能なものであることもできるので、次のことが成り立ちます：

```julia
inverse(t)(y) == inverse(t, y) == inverse(transform(t))(y)
```

!!! note
    `eltype(inverse(t, transform(t, x)))` は必ずしも `eltype(x)` と等しくなく、最も狭い可能な型であることが保証されておらず、バージョン間で警告なしに変更される可能性があります。コーナーケースでも合理的な具体的型を考え出すために努力がなされています。

