```
assemble!(
    self::SysmatAssemblerSparseDiag,
    mat::MT,
    dofnums_row::IV,
    dofnums_col::IV,
) where {MT, IV}
```

正方形対称対角行列を組み立てます。

  * `dofnums` = 行の自由度番号、列の自由度番号の入力は無視されます（行と列の番号は同じであると仮定されます）。
  * `mat` = **対角**正方行列
