```
feature_importances(model::M, fitresult, report)
```

与えられた `model` が内在的な特徴の重要性をサポートするモデルタイプ `M` の場合、モデルの `fitresult` と `report` から特徴の重要性を計算し、`feature::Symbol => importance::Real` のペアの抽象ベクトルとして返します（例: `[:gender =>0.23, :height =>0.7, :weight => 0.1]`）。

# 新しいモデルの実装

次のトレイトのオーバーロードも必要です: `MLJModelInterface.reports_feature_importances(::Type{<:M}) = true`

何らかの理由でモデルが時々特徴の重要性を報告できない場合、`feature_importances` はすべての重要性を 0.0 として返すべきです。例: `[:gender =>0.0, :height =>0.0, :weight => 0.0]`。
