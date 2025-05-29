`dist_lp(σ1, σ2, var; verbose, p, str_stat)`   

2つの軌道間のLp距離を計算する関数です。観測された各変数（`get_obs_var(σ)`に含まれる）に対してLp距離を計算し、これらの距離に統計量を適用します。`get_obs_var(σ1) == get_obs_var(σ2)`である必要があり、同じモデルからシミュレーションされたかどうかが検証されます。 ...

# 引数

  * `σ1::AbstractTrajectory` は最初の軌道です。σ2は2番目の軌道です。
  * `var::Symbol` は観測された変数です。`get_obs_var(σ1)`および`get_obs_var(σ2)`に含まれている必要があります。
  * `verbose::Bool` `true`の場合、計算の詳細な実行を開始します。

...
