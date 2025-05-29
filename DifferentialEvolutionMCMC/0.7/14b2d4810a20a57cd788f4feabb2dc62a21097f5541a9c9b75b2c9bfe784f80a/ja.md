```
optimize(model::DEModel, de::DE, ::MCMCThreads, n_iter::Int; progress=false, kwargs...)
```

最適なパラメータのセットを見つけます。

# 引数

  * `model`: データと事前分布を持つ尤度関数を含むモデル
  * `de`: 差分進化オブジェクト
  * `MCMCThreads`: 複数のスレッドで実行するためにMCMCThreads()オブジェクトを渡す
  * `n_iter`: イテレーションまたはサンプルの数

# キーワード

  * `progress=false`: アルゴリズムの進行状況を表示
  * `kwargs...`: オプションのキーワード引数
