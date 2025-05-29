```
SysmatAssemblerSparseDiag{T<:Number} <: AbstractSysmatAssembler
```

対称正方行列の対角行列を、対称正方行列の対角行列から組み立てるアセンブラです。

警告: 要素ごとの行列のオフ対角要素は、アセンブリ中に無視されます！

!!! note
    データ型のすべてのフィールドはプライベートです。この型は、`startassembly!`、`assemble!`、および `makematrix!` 関数によって操作されます。

