```
radon(image::AbstractMatrix, geometry::AbstractGeometry[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

明示的な幾何学を用いて `image` のラドン変換を計算します。アルゴリズムにはキーワード引数を通じて追加のパラメータを渡すことができます。関連するドキュメントを参照してください。デフォルトのアルゴリズムは [`Radon`](@ref) です。

関連項目: [`project_image`](@ref)
