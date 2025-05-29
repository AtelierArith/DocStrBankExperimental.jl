```
nvecs(X,n,r=0;flipsign=false,svds=false)
nvecs(X::ttensor,n,r=0;flipsign=false)
nvecs(X::ktensor,n,r=0;flipsign=false)
```

Computes the r leading singular vectors of mode-n matricization of a tensor X. Works with XₙXₙᵀ.

## Arguments:

  * `flipsign=true`: Make the largest magnitude element be positive.
  * `svds=true`: Use svds on Xₙ rather than eigs on XₙXₙᵀ.
