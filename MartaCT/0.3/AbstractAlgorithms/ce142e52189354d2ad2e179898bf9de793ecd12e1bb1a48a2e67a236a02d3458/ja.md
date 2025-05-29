```
iradon(sinog::AbstractMatrix[, geometry::AbstractGeometry[, params::AbstractParams[, algorithm::AbstractProjectionAlgorithm]]]; <keyword arguments>)
```

`sinog`の逆ラドン変換を明示的な幾何学で計算します。アルゴリズムが特定のパラメータを必要とする場合、これらは`params`で渡すことができます。追加のパラメータはキーワード引数を通じてアルゴリズムに渡すことができます。詳細については、それぞれのドキュメントを参照してください。デフォルトのアルゴリズムは[`FBP`](@ref)です。

関連情報: [`reconstruct_image`](@ref)
