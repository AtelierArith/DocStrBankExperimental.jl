```
reduction(red::Reduction,A::AbstractArray,args...) -> AbstractArray
reduction(red::Reduction,A::AbstractArray,X::AbstractSparseMatrix) -> AbstractArray
```

Given an array (of snapshots) `A`, returns a reduced basis obtained by means of the reduction strategy `red`
