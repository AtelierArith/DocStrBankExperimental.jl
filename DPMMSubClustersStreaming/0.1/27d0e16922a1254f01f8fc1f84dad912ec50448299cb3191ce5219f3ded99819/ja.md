```
fit(all_data::AbstractArray{Float32,2},local_hyper_params::distribution_hyper_params,α_param::Float32;
   iters::Int64 = 100, init_clusters::Int64 = 1,seed = nothing, verbose = true, save_model = false, burnout = 20, gt = nothing, max_clusters = Inf, outlier_weight = 0, outlier_params = nothing,smart_splits = false)
```

モデルを実行します（基本モード）。

# 引数とキーワード引数

  * `all_data::AbstractArray{Float32,2}` データを含む `DxN` 配列
  * `local_hyper_params::distribution_hyper_params` 事前ハイパーパラメータ
  * `α_param::Float32` 集中パラメータ
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
  * `smart_splits` スマートスプリットを使用する必要があります（ガウスのみ、デフォルトはfalse）

# 戻り値

  * `labels` ラベルの割り当て
  * `clusters` クラスタのパラメータ
  * `weights` クラスタの重み。`1` には合計しませんが、すべての未インスタンス化されたクラスタの重みを引いた `1` になります。
  * `iter_count` 各反復のタイミング
  * `nmi_score_history` 各反復のNMIスコア（gtが提供された場合）
  * `likelihood_history` 各反復の対数尤度。
  * `cluster_count_history` 各反復のクラスタ数。
  * `sub_labels` サブラベルの割り当て

# 例:

```julia
julia> x,y,clusters = generate_gaussian_data(10000,2,6,100.0)
...

julia> hyper_params = DPMMSubClusters.niw_hyperparams(1.0,
                  zeros(2),
                  5,
                  [1 0;0 1])
DPMMSubClusters.niw_hyperparams(1.0f0, Float32[0.0, 0.0], 5.0f0, Float32[1.0 0.0; 0.0 1.0])

julia> ret_values= fit(x,hyper_params,10.0, iters = 100, verbose=false)

...

julia> unique(ret_values[1])
6-element Array{Int64,1}:
 3
 6
 1
 2
 5
 4
```
