```
assemble!(
    self::SysmatAssemblerSparseHRZLumpingSymm,
    mat::MT,
    dofnums::IV,
    ignore::IV,
) where {MT, IV}
```

Assemble a HRZ-lumped square symmetric matrix.

Assembly of a HRZ-lumped square symmetric matrix. The method assembles the scaled diagonal of the square symmetric matrix using the two vectors of equation numbers for the rows and columns.
