```
modelmatrices(X::AbstractDesignMatrix)
modelmatrices(X::Vector{<:AbstractDesignMatrix})
modelmatrices(modelmatrix::AbstractMatrix)
```

イベントごとにモデル行列（デザイン行列とも呼ばれる）を個別に返します。これは `StatsModels.modelcols` に似ていますが、事前に計算されたデザイン行列にアクセスするだけです。デザイン行列を計算する必要がある場合は、`modelcols` を使用してください。

連続時間のケースでは、デザイン行列をさらに連結する `modelmatrix` と比較してください。
