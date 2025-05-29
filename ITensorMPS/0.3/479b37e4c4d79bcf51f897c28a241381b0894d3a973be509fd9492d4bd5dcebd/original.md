```
linkdim(M::MPS, j::Integer)
linkdim(M::MPO, j::Integer)
```

Get the dimension of the link or bond connecting the MPS or MPO tensor on site j to site j+1.

If there is no link Index, return `nothing`.
