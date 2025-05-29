```
S = NumberField(R)
```

Assert that R is a number field, and return a new data type `S` such that `S <: Number` and such that computations are more efficient than those happening in a QuotientRing.

Note: currently, this function does not fully prove that `Q` is a number field. If it isn't, arithmetic in the resulting ring will not give meaningful results.
