```
radon(image::AbstractMatrix, ts, ϕs[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

`image`のラドン変換を、ベクトル`ts`で与えられた積分点と、ベクトル`ϕs`で与えられた投影角を用いて計算します。アルゴリズムにはキーワード引数を通じて追加のパラメータを渡すことができます。関連するドキュメントを参照してください。デフォルトのアルゴリズムは[`Radon`](@ref)です。

関連項目: [`project_image`](@ref)
