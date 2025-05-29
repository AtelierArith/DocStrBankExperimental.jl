```
qn(i::QNIndex, b::Integer)
```

Returns the QN associated with block number `b` of a QNIndex `i`.

### Example

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> qn(i,1)
QN("Sz",-1)
julia> qn(i,2)
QN("Sz",0)
```
