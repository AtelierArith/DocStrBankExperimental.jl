```
CompositeBasis(b1, b2...)
```

Basis for composite Hilbert spaces.

Stores the subbases in a vector and creates the shape vector directly from the shape vectors of these subbases. Instead of creating a CompositeBasis directly `tensor(b1, b2...)` or `b1 ⊗ b2 ⊗ …` can be used.
