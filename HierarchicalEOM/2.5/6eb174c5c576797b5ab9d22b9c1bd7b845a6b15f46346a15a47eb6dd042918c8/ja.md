```
correlation_function(bath, tlist)
```

与えられたボソンバスと時間リストに対して相関関数 $C(t)$ を計算します。

## 入力ボソンバスが回転波近似 (RWA) を適用していない場合

$$
C(t)=\sum_{u=\textrm{R},\textrm{I}}(\delta_{u, \textrm{R}} + i\delta_{u, \textrm{I}})C^{u}(t)
$$

ここで

$$
C^{u}(t)=\sum_i \eta_i^u e^{-\gamma_i^u t}
$$

## 入力ボソンバスが回転波近似 (RWA) を適用している場合

$$
C^{\nu=\pm}(t)=\sum_i \eta_i^\nu e^{-\gamma_i^\nu t}
$$

# パラメータ

  * `bath::BosonBath` : 特定のボソンバスを記述するバスオブジェクト。
  * `tlist::AbstractVector`: 特定の時間。

# 戻り値 (RWAなし)

  * `clist::Vector{ComplexF64}` : 与えられた時間リストに従った相関関数の値のリスト。

# 戻り値 (RWAあり)

  * `cplist::Vector{ComplexF64}` : 与えられた時間リストに従った吸収 ($\nu=+$) 相関関数の値のリスト。
  * `cmlist::Vector{ComplexF64}` : 与えられた時間リストに従った放出 ($\nu=-$) 相関関数の値のリスト。
