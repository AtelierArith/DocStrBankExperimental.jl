```
sample(model::DEModel, de::DE, n_iter::Int; progress=false, kwargs...)
```

ポスターリ分布からサンプリングします。

# 引数

  * `model`: データと事前分布を持つ尤度関数を含むモデル
  * `de`: 差分進化オブジェクト
  * `n_iter`: イテレーションまたはサンプルの数

# キーワード

  * `progress=false`: サンプラーの進行状況を表示
  * `kwargs...`: オプションのキーワード引数
