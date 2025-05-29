```
radon(image::AbstractMatrix[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

`image`のラドン変換を、キーワード引数として与えられたパラメータで計算します。パラメータはアルゴリズムによって異なるため、関連するドキュメントを参照してください。デフォルトのアルゴリズムは[`Radon`](@ref)です。

関連情報: [`project_image`](@ref)
