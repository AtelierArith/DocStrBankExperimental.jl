```
blockdim(i::QNIndex, b::Integer)
```

Returns the dimension of block number `b` of a QNIndex `i`.

### Example

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> blockdim(i,1)
2
julia> blockdim(i,2)
4
```
