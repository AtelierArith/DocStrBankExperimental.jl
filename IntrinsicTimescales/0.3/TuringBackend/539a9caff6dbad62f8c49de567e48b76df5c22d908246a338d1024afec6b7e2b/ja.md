```
ADVIResults{T<:Real}
```

ADVI（自動微分変分推論）結果のコンテナ。

# フィールド

  * `samples::AbstractArray{T}`: 事後サンプルの行列
  * `MAP::AbstractVector{T}`: 最大事後推定
  * `variances::AbstractVector{T}`: 各パラメータの事後分散
  * `chain`: 完全な推論結果を含むTuringチェーンオブジェクト
