```
qn(i::QNIndex, b::Integer)
```

ブロック番号 `b` に関連付けられた QN を QNIndex `i` から返します。

### 例

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> qn(i,1)
QN("Sz",-1)
julia> qn(i,2)
QN("Sz",0)
```
