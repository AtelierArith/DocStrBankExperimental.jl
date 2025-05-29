### readpetsc(filename; int*type = nothing, scalar*type = nothing)

```
       :: Vector{Union{SparseMatrixCSC, Vector}}
```

`filename`からPETScのバイナリ形式でスパース行列を読み込みます。PETSC*DIRおよびPETSC*ARCHが使用されて、使用する正しい整数型と浮動小数点型が決定されます。`int_type`および`scalar_type`を使用して、これらの値を上書きすることができます。
