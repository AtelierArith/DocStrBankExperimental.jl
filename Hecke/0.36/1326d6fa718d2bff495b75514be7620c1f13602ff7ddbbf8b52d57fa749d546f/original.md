```
kernel(M::SMat{T}; side::Symbol = :left) where {T <: FieldElement}
```

Return a matrix $N$ containing a basis of the kernel of $M$. If `side` is `:left` (default), the left kernel is computed, i.e. the matrix of rows whose span gives the left kernel space. If `side` is `:right`, the right kernel is computed, i.e. the matrix of columns whose span is the right kernel space.
