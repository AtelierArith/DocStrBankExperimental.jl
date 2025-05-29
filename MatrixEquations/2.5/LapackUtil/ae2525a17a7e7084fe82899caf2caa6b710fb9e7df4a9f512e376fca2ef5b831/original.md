```
lanv2(A, B, C, D) -> (RT1R, RT1I, RT2R, RT2I, CS, SN)
```

Compute the Schur factorization of a real 2-by-2 nonsymmetric matrix `[A,B;C,D]` in standard form. `A`, `B`, `C`, `D` are overwritten on output by the corresponding elements of the standardised Schur form. `RT1R+im*RT1I` and `RT2R+im*RT2I` are the resulting eigenvalues. `CS` and `SN` are the parameters of the rotation matrix. Interface to the LAPACK subroutines DLANV2/SLANV2.
