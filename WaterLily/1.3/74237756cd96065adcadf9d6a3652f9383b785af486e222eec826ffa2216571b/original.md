```
mult!(p::Poisson,x)
```

Efficient function for Poisson matrix-vector multiplication.  Fills `p.z = p.A x` with 0 in the ghost cells.
