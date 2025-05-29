```
eliminate_dirichlet(A,dirichlet_marker)
```

Create a copy B of A sharing the sparsity pattern. Eliminate dirichlet nodes in B by setting 

```julia
    B[:,i]=0; B[i,:]=0; B[i,i]=1
```

for a node `i` marked as Dirichlet.

Returns B.
