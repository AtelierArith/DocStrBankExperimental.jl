```
assemble!(
    self::SysmatAssemblerSparseSymm,
    mat::MT,
    dofnums::IT,
    ignore
) where {MT, IT}
```

正方形対称行列を組み立てます。

`dofnums` は行の自由度番号であり、列の自由度番号の入力は無視されます（行番号と列番号は同じであると仮定されます）。
