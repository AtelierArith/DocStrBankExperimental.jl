```
feature_transform(I::AbstractArray{Bool, N}, [w=nothing]) -> F
```

バイナリ画像 `I` の特徴変換を計算し、`I` の各位置に対して最も近い「特徴」（`I` が `true` である位置）を見つけます。具体的には、`F[i]` は `I[F[i]]` が `true` である位置に最も近い `i` の位置をエンコードする `CartesianIndex` です。`i` からの距離が同じ特徴が `I` に複数ある場合は、任意の特徴が選ばれます。`I` に `true` の値がない場合、すべての位置は各座標が `typemin(Int)` であるインデックスにマッピングされます。

各座標に割り当てる重み `w` をオプションで指定できます。たとえば、`I` がボクセルが異方性の画像に対応する場合、`w` は各座標軸に沿ったボクセル間隔になる可能性があります。デフォルト値の `nothing` は `w=(1,1,...)` と同等です。

参照: [`distance_transform`](@ref).

# 引用

'A Linear Time Algorithm for Computing Exact Euclidean Distance Transforms of Binary Images in Arbitrary Dimensions' [Maurer et al., 2003](DOI: 10.1109/TPAMI.2003.1177156) ```
