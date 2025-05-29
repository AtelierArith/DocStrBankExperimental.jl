```
モデル(model, distr, link, pastObs, pastMean, X,
      external, zi)
```

カウントデータモデルを定義するためのラッパー関数。デフォルト設定は、回帰子やゼロインフレーションなしのIIDポアソンプロセスです。

構造体には以下のエントリがあります：

  * `distr`: "Poisson"、"Negative Binomial"、または "GPoisson"（INARMA用のベクトル）
  * `link`: 長さ2のベクトル、"Linear"または"Log"（INARMA用のベクトル）
  * `pastObs`: 自己回帰部分で考慮されるラグ
  * `pastMean`: MA/過去条件平均部分で考慮されるラグ
  * `X`: 回帰子の行列（行単位）
  * `external`: 回帰子が外部から入るかどうかのインジケーター
  * `zi`: インジケーター、ゼロインフレーション Y/N

# 例

```julia-repl
Model(pastObs = 1:2, pastMean = 1) # INGARCH(2, 1)
Model(pastObs = [1, 2], distr = "NegativeBinomial") # NB-INARCH(2)
Model(model = "INARMA", pastMean = 1, zi = true) # ゼロインフレートINMA(1)
```

詳細については、[Documentation](https://github.com/ManuelStapper/CountTimeSeries.jl/blob/master/CountTimeSeries_documentation.pdf)を参照してください。
