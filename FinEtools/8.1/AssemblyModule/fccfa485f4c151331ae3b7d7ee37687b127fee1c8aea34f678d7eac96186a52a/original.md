```
assemble!(
    self::SysmatAssemblerSparseDiag,
    mat::MT,
    dofnums_row::IV,
    dofnums_col::IV,
) where {MT, IV}
```

Assemble a square symmetric diagonal matrix.

  * `dofnums` = the row degree of freedom numbers, the column degree of freedom

number input is ignored (the row and column numbers are assumed to be the same).

  * `mat` = **diagonal** square matrix
