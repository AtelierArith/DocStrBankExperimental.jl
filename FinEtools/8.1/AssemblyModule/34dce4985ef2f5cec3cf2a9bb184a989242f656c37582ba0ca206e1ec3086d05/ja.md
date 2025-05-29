```
assemble!(
    self::SysmatAssemblerSparseHRZLumpingSymm,
    mat::MT,
    dofnums::IV,
    ignore::IV,
) where {MT, IV}
```

HRZラプされた正方対称行列を組み立てます。

HRZラプされた正方対称行列の組み立て。メソッドは、行と列の方程式番号の2つのベクトルを使用して、正方対称行列のスケーリングされた対角成分を組み立てます。
