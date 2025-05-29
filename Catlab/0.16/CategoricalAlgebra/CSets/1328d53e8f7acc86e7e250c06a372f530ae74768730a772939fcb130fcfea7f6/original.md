Check naturality condition for a purported ACSetTransformation, α: X→Y.  For each hom in the schema, e.g. h: m → n, the following square must commute:

```text
     αₘ
  Xₘ --> Yₘ
Xₕ ↓  ✓  ↓ Yₕ
  Xₙ --> Yₙ
     αₙ
```

You're allowed to run this on a named tuple partly specifying an ACSetTransformation, though at this time the domain and codomain must be fully specified ACSets.
