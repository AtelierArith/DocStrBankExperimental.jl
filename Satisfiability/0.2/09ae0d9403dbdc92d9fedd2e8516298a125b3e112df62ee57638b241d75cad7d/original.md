```
iff(z1::BoolExpr, z2::BoolExpr)
z1 ⟺ z2
```

Bidirectional implication between z1 and z2. Equivalent to `and(z1 ⟹ z2, z2 ⟹ z1)`.
