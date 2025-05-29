```
syst = similarity_transform(sys, T; unitary=false)
```

Perform a similarity transform `T : Tx̃ = x` on `sys` such that

```
Ã = T⁻¹AT
B̃ = T⁻¹ B
C̃ = CT
D̃ = D
```

If `unitary=true`, `T` is assumed unitary and the matrix adjoint is used instead of the inverse. See also [`balance_statespace`](@ref).
