```
Conversion_normalizedspace(S::Space, direction::Val{:forward} = Val(:forward))
```

`Conversion(S, normalizedspace(S))`を返します。これは直交多項式空間に対して具体的に推測できます。

```
Conversion_normalizedspace(S::Space, ::Val{:backward})
```

`Conversion(normalizedspace(S), S)`を返します。これは直交多項式空間に対して具体的に推測できます。
