```
eliminate_dirichlet!(A,dirichlet_marker)
```

Eliminate dirichlet nodes in matrix by setting 

```julia
    A[:,i]=0; A[i,:]=0; A[i,i]=1
```

for a node `i` marked as Dirichlet.

Returns A.
