```
DeltaMeta(method = ..., [ inverse = ... ])
```

`DeltaMeta` 構造体は、`DeltaFn` ノードにおける外向きメッセージの近似手法を指定します。

# 引数

  * `method`: 必須、近似手法、現在サポートされている手法は [`Linearization`](@ref)、[`Unscented`](@ref) および [`CVI`](@ref) です。
  * `inverse`: オプション、逆が提供されていない場合、逆伝播ルールは RTS (Petersen et al. 2018; On Approximate Delta Gaussian Message Passing on Factor Graphs) に基づいて計算されます。

`AbstractApproximationMethod` をデルタノードのメタに直接渡すことも可能です。この場合、`inverse` は `nothing` に設定されます。
