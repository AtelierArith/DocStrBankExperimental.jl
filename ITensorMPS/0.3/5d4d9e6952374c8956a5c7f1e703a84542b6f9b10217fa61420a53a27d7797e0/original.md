```
linkind(M::MPS, j::Integer)
linkind(M::MPO, j::Integer)
```

Get the link or bond Index connecting the MPS or MPO tensor on site j to site j+1.

If there is no link Index, return `nothing`.
