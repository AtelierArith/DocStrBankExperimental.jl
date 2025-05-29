`dist_lp(l_σ1, l_σ2; verbose, p, str_stat_list, str_stat_trajectory)` 

2つの任意の次元の軌道のセット間のLp距離を計算する関数。 ...

# 引数

  * `l_σ1::Vector{AbstractTrajectory}` は最初の軌道のセットです。l_σ2は2番目のものです。
  * `verbose::Bool` `true`の場合、計算の詳細な実行を開始します。
  * `str_stat_list::String` は、軌道の距離に適用する統計を設定することを可能にします。

これはクラスタリング分野ではリンク関数とも呼ばれます。現在のところ「平均」のみが利用可能です。 ...
