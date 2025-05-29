```
DitStr(dit::SubDitStr{D,N,T}) -> DitStr{D,N,T}
```

型 `SubDitStr` を `DitStr` に昇格させます。

```jldoctest
julia> x = DitStr{3, 5}(71)
02122 ₍₃₎

julia> sx =  SubDitStr(x, 2, 4)
SubDitStr{3, 5, Int64}(02122 ₍₃₎, 1, 3)

julia> DitStr(sx)
212 ₍₃₎
```
