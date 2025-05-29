```
blockdim(P::ProductSpace, c::Sector)
```

Return the total dimension of a coupled sector `c` in the product space, by summing over all `dim(P, s)` for all tuples of sectors `s::NTuple{N, <:Sector}` that can fuse to  `c`, counted with the correct multiplicity (i.e. number of ways in which `s` can fuse to `c`).

See also [`hasblock`](@ref) and [`blocksectors`](@ref).
