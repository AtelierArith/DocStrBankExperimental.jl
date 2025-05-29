```
pmmuladdsym(A, B, C, α, β)
```

Compute the symmetric periodic matrix `α*A + β*B*C`, where `α` and `β` are real scalars,  `A` is a symmetrix periodic matrix and the product `B*C` is known to be symmetric.  All matrix arguments may be constant matrices as well.

*Note:* This function is available only for periodic matrices of types `PeriodicArray`, `PeriodicMatrix`, `PeriodicFunctionMatrix` and `HarmonicArray`.
