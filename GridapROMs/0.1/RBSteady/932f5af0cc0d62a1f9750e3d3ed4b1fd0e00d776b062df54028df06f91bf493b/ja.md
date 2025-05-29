```
reduction(red::Reduction,A::AbstractArray,args...) -> AbstractArray
reduction(red::Reduction,A::AbstractArray,X::AbstractSparseMatrix) -> AbstractArray
```

配列（スナップショットの）`A`が与えられた場合、削減戦略`red`によって得られた削減基底を返します。
