```
blockdim(i::QNIndex, b::Integer)
```

QNIndex `i` のブロック番号 `b` の次元を返します。

### 例

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> blockdim(i,1)
2
julia> blockdim(i,2)
4
```
