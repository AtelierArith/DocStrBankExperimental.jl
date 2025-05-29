```
maxlinkdim(M::MPS)
maxlinkdim(M::MPO)
```

Get the maximum link dimension of the MPS or MPO.

The minimum this will return is `1`, even if there are no link indices.
