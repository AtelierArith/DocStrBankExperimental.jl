```
CRP(lrp_analyzer, layer, features)
```

特定の層における特徴に関してニューラルネットワークの出力を説明するために概念関連伝播を使用します。

# 引数

  * `lrp_analyzer::LRP`: LRPアナライザー
  * `layer::Int`: 概念が位置する層のインデックス
  * `features`: 説明する概念 / 特徴。

[`TopNFeatures`](@ref) および [`IndexedFeatures`](@ref) も参照してください。

# 参考文献

[1] R. Achtibat et al., From attribution maps to human-understandable explanations     through Concept Relevance Propagation
