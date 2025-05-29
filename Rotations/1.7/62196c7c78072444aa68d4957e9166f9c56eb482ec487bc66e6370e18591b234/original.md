```
(*)(q::QuatRotation, r::StaticVector)
```

Rotate a vector

Equivalent to `hmat()' lmult(q) * rmult(q)' hmat() * r`
