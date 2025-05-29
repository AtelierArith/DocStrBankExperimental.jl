```julia
abstract type PersonParameterAlgorithm
```

アイテム応答モデルの人パラメータの推定アルゴリズムを表す抽象型です。

各アルゴリズムは以下の関数を実装する必要があります：

  * [`optfun`](@ref): ルート探索アルゴリズムに渡される最適化関数
  * [`se`](@ref): 推定の標準誤差の計算。デフォルトは $1/\sqrt{I(\theta)}$ であり、ここで $I$ は $\theta$ におけるテスト情報です。
