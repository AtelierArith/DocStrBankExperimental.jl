```
precompute_R2sl([;TRF_min=100e-6, TRF_max=500e-6, T2s_min=5e-6, T2s_max=21e-6, ω1_max=π/TRF_max, B1_max=1.4, greens=greens_superlorentzian])
```

指定された引数によって指定された範囲内で線形化された `R2sl(TRF, α, B1, T2s)` とその導関数 `dR2sldB1(TRF, α, B1, T2s)`, `R2sldT2s(TRF, α, B1, T2s)` などを事前計算および補間します。

この関数は、指定された範囲内の孤立した半固体プールの一般化されたブロッホ方程式を解き、RFパルスの終わりでの `zs` の誤差を最小化する線形化された R2sl を計算し、異なるサンプル間で補間します。

# オプション引数:

  * `TRF_min::Real`: RFパルスの持続時間範囲の下限（秒単位）
  * `TRF_max::Real`: RFパルスの持続時間範囲の上限（秒単位）
  * `T2s_min::Real`: `T2s` 範囲の下限（秒単位）
  * `T2s_max::Real`: `T2s` 範囲の上限（秒単位）
  * `ω1_max::Real`: Rabi周波数 ω1 の上限、デフォルトは500μsのπパルスの周波数
  * `B1_max::Real`: B1範囲の上限、`B1 = 1` が完全にキャリブレーションされたRFフィールドに対応するように正規化
  * `greens=greens_superlorentzian`: Greens関数の形式 `G(κ) = G((t-τ)/T2s)`。このパッケージは、3つのGreens関数 `greens=greens_superlorentzian`（デフォルト）、`greens=greens_lorentzian`、および `greens=greens_gaussian` を提供します。

# 例

```jldoctest
julia> R2slT = precompute_R2sl();


julia> R2sl, dR2sldB1, R2sldT2s, _ = precompute_R2sl(TRF_min=100e-6, TRF_max=500e-6, T2s_min=5e-6, T2s_max=15e-6, ω1_max=π/500e-6, B1_max=1.4, greens=greens_gaussian);

```
