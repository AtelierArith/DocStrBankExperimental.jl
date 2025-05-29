```
margins = gain_phase_margins(g_ol, ω_c_guess=0.001, ω_g_guess=0.001)
```

閉ループの伝達関数 `g_ol::TransferFunction` が与えられたとき、臨界周波数（ラジアン / 時間）、ゲイン交差周波数（ラジアン / 時間）、ゲインマージン、および位相マージン（ラジアン）を計算します。

もし ω*c または ω*g が見つからない場合（すなわち、どちらかが `NaN` の場合）、しかし `bode_plot` が明確に臨界/ゲイン交差周波数を示している場合は、根を見つけるために `ω_c_guess` または `ω_g_guess` を調整します。

# 例

```
g_ol = 2 * exp(-s) / (5 * s + 1)
margins = gain_phase_margins(g_ol)
margins.ω_c # 臨界周波数（ラジアン / 時間）
margins.ω_g # ゲイン交差周波数（ラジアン / 時間）
margins.gain_margin # ゲインマージン
margins.phase_margin # 位相マージン（ラジアン）
```
