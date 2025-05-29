```
nblocks(i::QNIndex)
```

Returns the number of QN blocks, or subspaces, of the QNIndex `i`.

To obtain the dimension of block number `b`, use `blockdim(i,b)`. To obtain the QN associated with block `b`, use `qn(i,b)`.

### Example

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> nblocks(i)
3
```
