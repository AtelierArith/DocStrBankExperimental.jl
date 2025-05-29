```
ACWResults
```

ACW分析の入力と結果を保持する構造体。

# フィールド

  * `data::AbstractArray{<:Real}`: 入力時系列データ
  * `fs::Real`: サンプリング周波数
  * `acwtypes::Union{Vector{<:Symbol}, Symbol, Nothing}`: 計算するACWのタイプ
  * `n_lags::Union{Int, Nothing}`: ACF計算のためのラグの数
  * `freqlims::Union{Tuple{Real, Real}, Nothing}`: スペクトル分析のための周波数制限
  * `acw_results::Vector{<:Real}`: 計算されたACW値

# 注意事項

  * サポートされているACWタイプ: :acw0, :acw50, :acweuler, :tau, :knee
  * 結果の順序は入力のacwtypesの順序に一致します。
