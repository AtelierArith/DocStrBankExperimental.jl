```
sparse_matrix(A::MatElem; keepzrows::Bool = true)
```

Constructs the sparse matrix corresponding to the dense matrix $A$. If `keepzrows` is false, then the constructor will drop any zero row of $A$.
