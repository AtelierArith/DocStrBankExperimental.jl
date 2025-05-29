```
T4blockx(xs::VecOrMat{T}, ys::VecOrMat{T}, zs::VecOrMat{T}, orientation::Symbol = :a) where {T<:Number}
```

3Dブロックのグレーデッドテトラヘドラメッシュを生成します。

ノード間の非一様な間隔を持つ、規則的な配置の4ノードテトラヘドロンで、対角線の指定された向きを持ちます。

メッシュは、各論理的長方形セルを5または6のテトラヘドロンに分割することによって生成されます：`T4block`を参照してください。
