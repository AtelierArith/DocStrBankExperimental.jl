```
fourier_approx(d, H, P; pc=1, cc=1, N=10, M=1, g=9.81)
```

水深 `d` で伝播する高さ `H` と長さ `L` の定常波の近似解 `u` をフーリエ近似法を用いて求めます。

# 引数

  * `d`: 水深 (m)
  * `H`: 波の高さ (m)
  * `P`: 波のパラメータ - 長さ `L` (m) または周期 `T` (s)
  * `pc`: パラメータ基準; `pc=1` - 長さ (デフォルト), `pc=2` - 周期
  * `cc`: 流れの基準; `cc=1` - ストークス (デフォルト), `cc=2` - オイラー
  * `N`: 解の固有値の数、デフォルトは `N=10`
  * `M`: 高さのステップ数、デフォルトは `M=1`
  * `g`: 重力加速度 (m/s^2)、デフォルトは `g=9.81`

# 出力

  * `u[1:N+1]`: 自由表面の上昇 *kη*
  * `u[N+2:2N+1]`: 流れ関数の係数 *B*
  * `u[2N+2]`: 波の速さ *c√(k/g)*
  * `u[2N+3]`: 平均水深 *kη̄*
  * `u[2N+4]`: 波による体積フラックス *q√(k³/g)*
  * `u[2N+5]`: ベルヌーイ定数 *rk/g*
  * `u[2N+6]`: 平均流速 *Ū√(k/g)*
  * `u[2N+7]`: 波の高さ *kH*
