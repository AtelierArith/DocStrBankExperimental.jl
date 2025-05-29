```
rotate!(bridge::BridgeRotation, A::AbstractVector, tailpos::Integer)
```

Rotates `A` on `tailpos` using a small extra memory. ≤ a third of A and ≤ than n+n/3 copy-write ops.
