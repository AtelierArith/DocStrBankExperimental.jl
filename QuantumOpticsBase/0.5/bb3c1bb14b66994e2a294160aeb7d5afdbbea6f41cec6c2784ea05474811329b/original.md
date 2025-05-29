```
displace_analytical!(op, alpha::Number)
```

Overwrite, in place, the matrix elements of the FockBasis operator `op`, so that it is equal to `displace_analytical(eltype(op), basis(op), alpha)`
