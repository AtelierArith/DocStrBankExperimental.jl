```
nblocks(i::QNIndex)
```

QNIndex `i` の QN ブロックまたは部分空間の数を返します。

ブロック番号 `b` の次元を取得するには、`blockdim(i,b)` を使用します。ブロック `b` に関連する QN を取得するには、`qn(i,b)` を使用します。

### 例

```
julia> i = Index([QN("Sz",-1)=>2, QN("Sz",0)=>4, QN("Sz",1)=>2], "i")
julia> nblocks(i)
3
```
