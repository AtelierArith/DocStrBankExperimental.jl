```
M = bitinformation(A::AbstractArray{T}, mask::BitArray) where {T<:Union{Integer,AbstractFloat}}
```

配列 `A` のビット単位の実情報量は、次元 `dim`（オプションのキーワード）に沿った `A` の隣接エントリ間のビット単位の相互情報量から計算されます。配列 `A` は、マスク `mask` のエントリ内の真の値によってマスクされます。マスクされた要素は、ビット単位の情報計算では無視されます。
