```
assemble!(
    self::SysmatAssemblerSparseSymm,
    mat::MT,
    dofnums::IT,
    ignore
) where {MT, IT}
```

Assemble a square symmetric matrix.

`dofnums` are the row degree of freedom numbers, the column degree of freedom number input is ignored (the row and column numbers are assumed to be the same).
