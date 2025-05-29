```
dp_parallel(all_data::AbstractArray{Float32,2},
    local_hyper_params::distribution_hyper_params,
    α_param::Float32,
     iters::Int64 = 100,
     init_clusters::Int64 = 1,
     seed = nothing,
     verbose = true,
     save_model = false,
     burnout = 15,
     gt = nothing,
     max_clusters = Inf,
     outlier_weight = 0,
     outlier_params = nothing)
```

モデルを実行します。

# 引数とキーワード引数

  * `all_data::AbstractArray{Float32,2}` データを含む `DxN` 配列
  * `local_hyper_params::distribution_hyper_params` 事前ハイパーパラメータ
  * `α_param::Float32` 集中度パラメータ
  * `iters::Int64` モデルを実行する反復回数
  * `init_clusters::Int64` 初期クラスタの数
  * `seed` すべてのワーカーで使用されるランダムシードを定義します。使用する場合は、`@everywhere using random` の前に置く必要があります。
  * `verbose` 各反復で印刷を行います。
  * `save_model` 25回の反復ごとにチェックポイントを保存します。
  * `burnout` クラスタを作成した後、分割/マージを許可するまでの待機時間
  * `gt` グラウンドトゥルース。提供されると、各反復でNMIおよびVI分析を実行します。
  * `max_clusters` クラスタの数を制限します
  * `outlier_weight` 追加の非分割コンポーネントの定数重み
  * `outlier_params` 追加の非分割コンポーネントのハイパーパラメータ

# 戻り値

dp*model, iter*count , nmi*score*history, liklihood*history, cluster*count_history

  * `dp_model` 推定されたDPMMモデル
  * `iter_count` 各反復のタイミング
  * `nmi_score_history` 各反復のNMIスコア（gtが提供された場合）
  * `likelihood_history` 各反復の対数尤度。
  * `cluster_count_history` 各反復のクラスタ数。
