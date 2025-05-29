```
iradon(sinog::AbstractMatrix[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

`sinog`の逆ラドン変換を、キーワード引数として与えられたパラメータで計算します。パラメータはアルゴリズムに依存しますので、関連するドキュメントを参照してください。デフォルトのアルゴリズムは[`FBP`](@ref)です。

関連情報: [`reconstruct_image`](@ref)
