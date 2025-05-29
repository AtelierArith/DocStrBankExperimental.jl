```
catchaMouse16(𝐱::Vector)
catchaMouse16(X::Array)
catchaMouse16[featurename::Symbol](X::Array)
```

時系列ベクトル `𝐱` または配列 `X` の列に対してすべての特徴を評価します。`catchaMouse16` は FeatureSet であり、特徴名（シンボル）でインデックスを付けることで利用可能な特徴のサブセットを返すことができます。`getnames(catchaMouse16)`、`getkeywords(catchaMouse16)` および `getdescriptions(catchaMouse16)` はそれぞれ特徴名、キーワード、説明を返します。特徴は `FeatureArray` で返され、配列の行は特徴名で注釈が付けられます。`FeatureArray` は `Array(F)` を使って通常の配列に変換できます。

# 例

```julia
𝐱 = CatchaMouse16.testdata[:test]
𝐟 = catchaMouse16(𝐱)

X = randn(100, 10)
F = catchaMouse16(X)
F = catchaMouse16[:AC_nl_035](X)
```
