```
SysmatAssemblerSparse{IT, MBT, IBT} <: AbstractSysmatAssembler
```

要素ごとの行列からスパースグローバル行列を組み立てるための型です。

!!! note
    データ型のすべてのフィールドはプライベートです。この型は、`startassembly!`、`assemble!`、および `makematrix!` 関数によって操作されます。

