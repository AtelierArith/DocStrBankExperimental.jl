```
TTtv(X::TTtensor,u::VectorCell,mode::Int)
TTtv(X::TTtensor,U::AbstractMatrix{<:Number},mode::Int)
TTtv(X::CoreCell,u::VectorCell)
TTtv(X::CoreCell,U::AbstractMatrix{<:Number})
```

TT-tensor times vector. For N=ndims(X) and n=[mode,mode+1,...,N] contracts nth core of the TT-tensor with vector u[N-n+1]. If input is a matrix, then vectors u are its columns. Called on a subset of cores, it contracts all given cores to vectors.
