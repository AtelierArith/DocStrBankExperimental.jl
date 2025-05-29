```
NeXLUncertainties.asa(::Type{DataFrame}, ffrs::AbstractVector{<:FitResult}; charOnly = true, withUnc = false, format = :normal # :pivot or :long)
```

汎用の `FitResult` を DataFrame として返します。

フォーマット:

  * :normal - スペクトルごとに1行、k比ごとに1列
  * :pivot - ROIごとに1行、スペクトルごとに1列（オプション: k比の1σ不確かさの列）
  * :long - スペクトルごとに1行、特徴、測定されたk比
