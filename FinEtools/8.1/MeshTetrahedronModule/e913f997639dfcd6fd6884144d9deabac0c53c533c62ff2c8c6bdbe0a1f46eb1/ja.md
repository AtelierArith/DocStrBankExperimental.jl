```
T10blockx(xs::VecOrMat{T}, ys::VecOrMat{T}, zs::VecOrMat{T}, orientation::Symbol = :a) where {T<:Number}
```

3Dブロックの10ノード四面体メッシュを生成します。

ノード間の非一様な間隔を持つ、規則的に配置された10ノード四面体で、対角線の指定された向きを持ちます。

メッシュは、各論理的な長方形セルを6つの四面体に分割することによって生成されます。
