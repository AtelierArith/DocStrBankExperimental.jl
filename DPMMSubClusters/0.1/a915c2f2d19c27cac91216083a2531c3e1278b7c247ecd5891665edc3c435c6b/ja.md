```
dp_parallel(model_params::String; verbose = true, save_model = true,burnout = 5, gt = nothing)
```

モデルを高度なモードで実行します。

# 引数とキーワード引数

  * `model_params::String` パラメータファイルへのパス（下記参照）
  * `verbose` 各イテレーションで出力を行います。
  * `save_model` パラメータファイルで指定された `X` イテレーションごとにチェックポイントを保存します。
  * `burnout` クラスターを作成した後、分割/マージを許可するまでの待機時間
  * `gt` グラウンドトゥルース。提供されると、各イテレーションでNMIおよびVI分析を実行します。

# 戻り値

dp*model, iter*count , nmi*score*history, liklihood*history, cluster*count_history

  * `dp_model` 推定されたDPMMモデル
  * `iter_count` 各イテレーションのタイミング
  * `nmi_score_history` 各イテレーションのNMIスコア（gtが提供された場合）
  * `likelihood_history` 各イテレーションの対数尤度。
  * `cluster_count_history` 各イテレーションのクラスター数。
