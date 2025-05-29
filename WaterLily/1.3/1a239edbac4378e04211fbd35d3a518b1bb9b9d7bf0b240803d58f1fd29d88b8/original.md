```
BC!(a,A)
```

Apply boundary conditions to the ghost cells of a *vector* field. A Dirichlet condition `a[I,i]=A[i]` is applied to the vector component *normal* to the domain boundary. For example `aₓ(x)=Aₓ ∀ x ∈ minmax(X)`. A zero Neumann condition is applied to the tangential components.
