```
dmvec(D)
```

Antisymmetric matrix representation of the Dzyaloshinskii-Moriya pseudo-vector,

```
  [  0    D[3] -D[2]
   -D[3]   0    D[1]
    D[2] -D[1]   0  ]
```

By construction, `Si'*dmvec(D)*Sj ≈ D⋅(Si×Sj)` for any dipoles `Si` and `Sj`. This helper function is intended for use with [`set_exchange!`](@ref).
