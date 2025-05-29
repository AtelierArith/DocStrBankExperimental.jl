```
compare(a, b, order::Type{<:AbstractMonomialOrdering})
```

`a < b` の場合は負の数を、`a > b` の場合は正の数を、`a == b` の場合はゼロを返します。比較は `order` に従って行われます。

**警告** これは非推奨です。代わりに `cmp(order(), a, b)` を使用してください。
