```
distance_transform(F::AbstractArray{CartesianIndex}, [w=nothing]) -> D
```

`F`の距離変換を計算します。ここで、各要素`F[i]`は`i`に割り当てられた「ターゲット」または「特徴」位置を表します。具体的には、`D[i]`は`i`と`F[i]`の間の距離です。各座標に割り当てられる重み`w`をオプションで指定できます。デフォルト値の`nothing`は`w=(1,1,...)`と同等です。

参照: [`feature_transform`](@ref).
