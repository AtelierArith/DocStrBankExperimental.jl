```
matrix_colors(A::Union{Array,UpperTriangular,LowerTriangular})
```

The color vector for dense matrix and triangular matrix is simply `[1,2,3,..., Base.size(A,2)]`.
