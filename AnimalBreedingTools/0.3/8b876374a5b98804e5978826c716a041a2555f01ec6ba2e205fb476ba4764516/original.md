```
dv,ev = ldlt_symtrid(T::SymTridiagonal)
```

Calculate the LDLT factor of a symmetric tridiagonal matrix. Note that the factor is a lower tridiagonal matrix, and the output is a couple of vectors. The factor is stored in `dv` for the diagonal matrix (D) and in `ev` for the off-diagonal elements (L).
