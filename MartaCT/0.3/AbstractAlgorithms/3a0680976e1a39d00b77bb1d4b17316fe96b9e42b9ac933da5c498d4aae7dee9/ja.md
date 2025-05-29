```
iradon(sinog::AbstractMatrix, xs[, ys[, algorithm::AbstractProjectionAlgorithm[, coo::AbstractCoordinates]]]; <keyword arguments>)
```

`sinog`の逆ラドン変換を、ベクトル`xs`と`ys`で指定された点で計算します。`ys`が省略された場合、再構成は`xs == ys`の正方形で行われます。デフォルトの再構成アルゴリズムは[`FBP`](@ref)です。追加のパラメータについては、該当するドキュメントを参照してください。

関連情報: [`reconstruct_image`](@ref)
