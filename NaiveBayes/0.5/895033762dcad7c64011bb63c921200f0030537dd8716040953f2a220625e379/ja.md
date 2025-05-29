`HybridNB`モデルを連続および/または離散特徴で初期化します

### コンストラクタ

```julia
HybridNB(labels::AbstractVector, kde_names::AbstractVector, discrete_names::AbstractVector)
HybridNB(labels::AbstractVector, kde_names::AbstractVector)
HybridNB(labels::AbstractVector, num_kde::Int, num_discrete::Int)
```

### 引数

  * `labels` : 特徴ラベルのAbstractVector{Any}
  * `kde_names` : 連続特徴の名前のAbstractVector{Any}
  * `discrete_names` : 離散特徴の名前のAbstractVector{Any}
  * `num_kde` : 連続特徴の数
  * `num_discrete` : 離散特徴の数
