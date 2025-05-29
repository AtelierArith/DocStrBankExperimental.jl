```
stepwise(df; dv, iv, sv, dir, output, measure)
```

前方または後方のステップワイズ回帰を実行します。

# 引数

  * `df::DataFrame`: データセット
  * `dv::T`: 従属変数の名前
  * `iv::Vector{T}`: 独立変数のリスト
  * `sv::T`: すべてのモデルに含まれる静的変数 (dv ~ sv + sum(iv))
  * `dir::Symbol=:f`: モデリングの方向:

      * `:f`: 前方
      * `:b`: 後方
  * `output::Bool=false`: true の場合、回帰の詳細を出力
  * `measure::Symbol=:r2`: パフォーマンス評価に使用される測定:

      * `:r2`: 調整済み R²
      * `:aic`: 赤池情報量基準
      * `:bic`: ベイズ情報量基準
  * `acc::Symbol=:cpu`: CPU (デフォルト) または GPU アクセラレーションを使用:

      * `:cpu`
      * `:cuda`
      * `:metal`
  * `alpha::Float64=0.05`: 有意水準
  * `checkp::Bool=false`: true の場合、変数はモデルの P 値が `alpha` で設定された有意水準よりも小さい場合にのみモデルに追加/保持される

# 戻り値

  * `best_model::Vector{T}`: 最良モデルの変数のリスト
