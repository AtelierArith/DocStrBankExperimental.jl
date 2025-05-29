```
SysmatAssemblerSparseHRZLumpingSymm{IT, MBT, IBT} <: AbstractSysmatAssembler
```

**対称的なラプトスクエア**行列を**対称的なスクエア**行列から組み立てるアセンブラ。

参考文献: 質量ラプトと有限要素法における関連プロセスに関するノート, E. Hinton, T. Rock, O. C. Zienkiewicz, Earthquake Engineering & Structural Dynamics, volume 4, number 3, 245–249, 1976.

!!! note
    データ型のすべてのフィールドはプライベートです。この型は、`startassembly!`、`assemble!`、および`makematrix!`関数によって操作されます。


!!! note
    このアセンブラは対角化された質量行列を計算および組み立てることができます。ただし、質量行列のエントリの意味が異なる場合（平行移動と回転）、質量行列は正しく計算されません。率直に言えば：これは均質な質量行列、たとえばすべての平行移動自由度にのみ使用できます。

