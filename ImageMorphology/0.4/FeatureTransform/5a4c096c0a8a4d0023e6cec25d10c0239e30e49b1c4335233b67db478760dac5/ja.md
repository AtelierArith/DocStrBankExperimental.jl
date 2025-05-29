```
feature_transform(img::AbstractArray{Bool, N};
                  weights=nothing, nthreads=Threads.nthreads()) -> F
```

バイナリ画像 `I` の特徴変換を計算し、`I` の各位置に対して最も近い「特徴」（`I` が `true` である位置）を見つけます。具体的には、`F[i]` は `I[F[i]]` が `true` である位置に最も近い `i` の位置をエンコードする `CartesianIndex` です。`i` からの距離が同じ特徴が `I` に複数ある場合は、任意の特徴が選ばれます。`I` に `true` の値がない場合、すべての位置は各座標が `typemin(Int)` であるインデックスにマッピングされます。

各座標に割り当てられる重み `w` をオプションで指定できます。たとえば、`I` がボクセルが異方性の画像に対応する場合、`w` は各座標軸に沿ったボクセル間隔になる可能性があります。デフォルト値の `nothing` は `w=(1,1,...)` と同等です。

参照: [`distance_transform`](@ref).

# 引用

  * [1] Maurer, Calvin R., Rensheng Qi, and Vijay Raghavan. "A linear time algorithm for computing exact Euclidean distance transforms of binary images in arbitrary dimensions." *IEEE Transactions on Pattern Analysis and Machine Intelligence* 25.2 (2003): 265-270.
