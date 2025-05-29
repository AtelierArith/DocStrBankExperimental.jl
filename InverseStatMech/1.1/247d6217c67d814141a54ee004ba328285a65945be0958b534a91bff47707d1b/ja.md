```
reverse_mc(dim::Int, n::Int, ρ::Float64, g2_targ::Function; initial_box = missing, bin_size = 0.05, range = 5, sweeps = 100, displace = 0.1, t_i = 1, t_f = 0.001, cooling_rate = 0.98)
```

逆モンテカルロアルゴリズムは、ターゲットペア相関関数 $g_2(r)$ を生成する平衡構成を生成します。

# 引数

  * `dim::Int`: システムの次元。
  * `n::Int`: 粒子の数。
  * `ρ::Float64`: 粒子の数密度。
  * `g2_targ::Function`: 関数 `g2_targ(r)` としてのターゲットペア相関関数。

# キーワード引数

  * `initial_box::Box` (オプション): 初期構成ボックス。デフォルトは `missing` で、ランダムなボックスを生成します。
  * `bin_size::Float64` (オプション): ペア相関関数を計算するためのビンサイズ。デフォルトは 0.05。
  * `range::Float64` (オプション): 相互作用ポテンシャルの範囲。デフォルトは 5。
  * `sweeps::Int` (オプション): 各温度でのモンテカルロスイープの数。デフォルトは 100。
  * `displace::Float64` (オプション): 粒子移動の最大変位。デフォルトは 0.1。
  * `t_i::Float64` (オプション): 初期温度。デフォルトは 1。
  * `t_f::Float64` (オプション): 最終温度。デフォルトは 0.001。
  * `cooling_rate::Float64` (オプション): 温度低下の冷却率。デフォルトは 0.98。

# 戻り値

  * `b::Box`: 生成された平衡古典構成ボックス。粒子の位置を取得するには `b.particles'` を使用します。

# 例

```
box = InverseStatMech.reverse_mc(2, 100, 0.5, r -> 1 - exp(-π*r^2))
```
