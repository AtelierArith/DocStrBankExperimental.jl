```
jordan_block(expr,square_size::Integer)
```

Computes the square Jordan block matrix `J` of dimension `square_size`.

The entries of `J` are `J[i,i] = expr` for i = 1,...,n, `J[i,i+1] = 1` for i = 1,...,n-1, and all other entries are 0.
