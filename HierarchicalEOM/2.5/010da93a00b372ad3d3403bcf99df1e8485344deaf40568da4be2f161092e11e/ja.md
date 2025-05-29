```
correlation_function(bath, tlist)
```

与えられたフェルミオンバスと時間リストに対して相関関数 $C^{\nu=+}(t)$ と $C^{\nu=-}(t)$ を計算します。ここで、$\nu=+$ は吸収過程を表し、$\nu=-$ は放出過程を表します。

$$
C^{\nu=\pm}(t)=\sum_i \eta_i^\nu e^{-\gamma_i^\nu t}
$$

# パラメータ

  * `bath::FermionBath` : 特定のフェルミオンバスを記述するバスオブジェクト。
  * `tlist::AbstractVector`: 特定の時間。

# 戻り値

  * `cplist::Vector{ComplexF64}` : 与えられた時間リストに従った吸収 ($\nu=+$) 相関関数の値のリスト。
  * `cmlist::Vector{ComplexF64}` : 与えられた時間リストに従った放出 ($\nu=-$) 相関関数の値のリスト。
