```
modelX_gaussian_group_knockoffs(X, method, groups, μ, Σ; [m], [covariance_approximator], [kwargs])
modelX_gaussian_group_knockoffs(X, method, groups; [m], [covariance_approximator], [kwargs])
```

ガウスモデル-Xグループノックオフを構築します。共分散 `Σ` と平均 `μ` が指定されていない場合、データから推定されます。つまり、第二次のグループノックオフを作成します。グループ構造を組み込むために、（真のまたは推定された）共分散行列は `groups` メンバーシップに従ってブロック対角化され、緩和された最適化問題を解決します。詳細については、参考文献とKnockoffs.jlのドキュメントを参照してください。

# 入力

  * `X`: `n × p` デザイン行列。各行はサンプル、各列は特徴です。
  * `method`: ノックオフを構築するための方法。オプションには以下が含まれます。

      * `:maxent`: （推奨）完全一般的最大エントロピーグループノックオフのため
      * `:mvr`: 完全一般的最小分散ベースの再構成可能性（MVR）グループノックオフのため
      * `:equi`: 等相関ノックオフのため。これは `Dai R, Barber R. The knockoff filter for FDR control in group-sparse and multitask regression. International conference on machine learning 2016 Jun 11 (pp. 1851-1859). PMLR.` で提案された方法論です。
      * `:sdp`: 座標降下に基づく完全一般的SDPグループノックオフ
      * `:sdp_block`: 各ブロックが内部点ソルバーを使用して正確に解かれる完全一般的SDPグループノックオフ。
      * `:sdp_subopt`: 各ブロック `S_{i} = γ_i * Σ_{ii}` を選択します。これはDaiとBarber 2016で提案された等相関グループノックオフのアイデアをわずかに一般化します。
  * `groups`: グループメンバーシップのベクトル
  * `μ`: `X` の真の列平均を格納する長さ `p` のベクトル
  * `Σ`: `X` の列のための `p × p` 共分散行列
  * `m`: 変数ごとのノックオフの数、デフォルトは1。
  * `covariance_approximator`: 共分散推定器、デフォルトは `LinearShrinkage(DiagonalUnequalVariance(), :lw)`。詳細なオプションについてはCovarianceEstimation.jlを参照してください。
  * `kwargs`: `solve_s_group` のための追加のキーワード引数

# グループの定義方法

エクスポートされた関数 `hc_partition_groups` を使用してグループメンバーシップベクトルを構築できます。

# 計算時間に関する注意

グループノックオフの計算複雑性はグループサイズに対して二次的にスケールします。したがって、非常に大きなグループ（例：グループごとに100人以上のメンバー）は、パラメータ推定を劇的に遅くします。そのような場合、各グループからトップ代表者を選択してグループノックオフを構築する `modelX_gaussian_rep_group_knockoffs` を実行することを検討できます。

# 参考文献

Dai & Barber 2016, The knockoff filter for FDR control in group-sparse and multitask regression
