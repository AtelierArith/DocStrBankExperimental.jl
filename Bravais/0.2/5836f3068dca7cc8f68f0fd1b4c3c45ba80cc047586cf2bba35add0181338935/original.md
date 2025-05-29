```
bravaistype(sgnum::Integer, D::Integer=3; normalize::Bool=false)  -->  String
```

Return the Bravais type of `sgnum` in dimension `D` as a string (as the concatenation of the single-character crystal abbreviation and the centering type).

## Keyword arguments

  * **`normalize`:** If the centering type associated with `sgnum` is `'A'`, we can choose (depending on the keyword argument `normalize`, defaulting to `false`) to "normalize" to the centering type `'C'`, since the difference between `'A'` and `'C'` centering only amounts to a basis change. With `normalize=true` we then have only the canonical 14 Bravais type, i.e.  `unique(bravaistype.(1:230, 3), normalize=true)` returns only 14 distinct types, rather than 15.

    This only affects space groups 38-41 (normalizing their conventional Bravais types from `"oA"` to `"oC"`).
