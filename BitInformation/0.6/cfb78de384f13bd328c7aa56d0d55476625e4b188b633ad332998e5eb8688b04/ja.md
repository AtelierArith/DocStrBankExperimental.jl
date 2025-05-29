```
R = redundancy(A::AbstractArray{T},B::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

2つの配列A,Bのビット単位の冗長性。冗長性は相互情報量の正規化された尺度であり、常に同一/反対のビットの場合は1、相互情報がない場合は0です。
