```
sample(model::DEModel, de::DE, ::MCMCThreads, n_iter::Int; progress=false, kwargs...)
```

各粒子群が変異および交差ステップのために別々のスレッドで実行される後方分布からサンプリングします。

# 引数

  * `model`: データと事前分布を持つ尤度関数を含むモデル
  * `de`: 差分進化オブジェクト
  * `MCMCThreads`: 複数のスレッドで実行するためにMCMCThreads()オブジェクトを渡す
  * `n_iter`: 繰り返し回数またはサンプル数

# キーワード

  * `progress=false`: サンプラーの進行状況を表示
  * `kwargs...`: オプションのキーワード引数
