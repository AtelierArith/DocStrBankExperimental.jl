```
catch22(𝐱::Vector)
catch22(X::Array)
catch22[featurename::Symbol](X::Array)
```

時系列ベクトル `𝐱` または配列 `X` の列に対してすべての特徴を評価します。`catch22` は FeatureSet であり、特徴名（シンボル）でインデックス指定することで利用可能な特徴のサブセットを返すことができます。`getnames(catch22)`、`getkeywords(catch22)` および `getdescriptions(catch22)` はそれぞれ特徴名、キーワード、説明を返します。特徴は `FeatureArray` で返され、配列の行は特徴名で注釈が付けられています。`FeatureArray` は `Array(F)` を使って通常の配列に変換できます。

# 例

```julia
𝐱 = Catch22.testdata[:test]
𝐟 = catch22(𝐱)

X = randn(100, 10)
F = catch22(X)
F = catch22[:DN_HistogramMode_5](X)
```
