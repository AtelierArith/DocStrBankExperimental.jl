```
optim_parametrized_pot(my_params, pot, dim, ρ, targ_g2, targ_s; 
    large_r_grid = missing, n::Int = 600, bin_size::Float64 = 0.05, r_range::Float64 = 10, k_range::Float64 = 10,
    g2_weight_range::Float64 = 2, s_weight_range::Float64 = 4, 
    n_threads::Int = 15, configs_per_thread::Int = 10, displace = 0.2, Ψ_tol::Float64 = 0.005, show_pb::Bool = true, test::Bool = false)
```

トルカート・ワンアルゴリズムを使用して、ターゲットペア相関関数と構造因子に一致させるためにポテンシャルパラメータの反復最適化を行います。

## 引数

  * `my_params::Vector{Float64}`: 初期ポテンシャルパラメータのベクトル。
  * `pot::Function`: 粒子間の相互作用ポテンシャルを計算するポテンシャル関数。
  * `dim::Int`: システムの次元。
  * `ρ::Float64`: システムの密度。
  * `targ_g2::Function`: ターゲットペア相関関数を表す関数。距離値 `r` を受け取り、その距離でのターゲット g2 値を返します。
  * `targ_s::Function`: ターゲット構造因子を表す関数。波ベクトル `k` を受け取り、その波ベクトルでのターゲット S 値を返します。

## キーワード引数（すべてオプション）

  * `large_r_grid::Missing`: 長距離ポテンシャルの計算のための大きな r グリッド。デフォルト値は `missing`。
  * `n::Int`: シミュレーションのためのボックスの数。デフォルト値は `600`。
  * `bin_size::Float64`: ペア相関関数と構造因子計算のためのビンのサイズ。デフォルト値は `0.05`。
  * `r_range::Float64`: ペア相関関数計算のための r 値の範囲。デフォルト値は `10`。
  * `k_range::Float64`: 構造因子計算のための k 値の範囲。デフォルト値は `10`。
  * `g2_weight_range::Float64`: 目的関数におけるペア相関関数の重み範囲。デフォルト値は `2`。
  * `s_weight_range::Float64`: 目的関数における構造因子の重み範囲。デフォルト値は `4`。
  * `n_threads::Int`: 並列計算のためのスレッド数。デフォルト値は `15`。
  * `configs_per_thread::Int`: シミュレーションのためにスレッドごとに生成する構成の数。デフォルト値は `10`。
  * `displace::Float64`: メトロポリスモンテカルロシミュレーションにおけるキックサイズ。デフォルト値は `0.2`。
  * `Ψ_tol::Float64`: 目的関数の収束のための許容誤差。デフォルト値は `0.005`。
  * `show_pb::Bool`: シミュレーション中にプログレスバーを表示するかどうかを示すブール値。デフォルト値は `true`。
  * `test::Bool`: テスト実行であるかどうかを示し、収束を示すブール値を返すフラグ。デフォルト値は `false`。

## 戻り値

  * `test` が true の場合、収束が達成された場合は `true` を返し、そうでない場合は `false` を返します。
  * `test` が false の場合、最適化されたポテンシャルパラメータを返します。

## 例

```
#ペアポテンシャルの形式
pot(r, params) = params[1]*exp(-(r/params[2])^2)

#初期推定パラメータ
my_params = [1.0, 2.0] #これは Float64 であることを示すために 1 の代わりに 1.0 と書きます

#ターゲットペア相関関数と構造因子
targ_g2(r) = 1 
targ_s(r) = 1

#パラメータを最適化する
InverseStatMech.optim_parametrized_pot(my_params, pot, 2, 1, targ_g2, targ_s)
```
