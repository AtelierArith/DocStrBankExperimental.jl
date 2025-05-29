```
initial_condition_density_wave(x, t, equations::CompressibleEulerEquations1D)
```

定常速度と圧力を持つ密度の正弦波; 圧縮性オイラー方程式を線形輸送方程式に還元します。この設定は、論文からのECフラックスの安定性のテストケースです。

  * Gregor J. Gassner, Magnus Svärd, Florian J. Hindenlang (2020) エントロピー安定および/または分割形式の高次スキームの安定性の問題 [arXiv: 2007.09026](https://arxiv.org/abs/2007.09026)

以下のパラメータで

  * ドメイン [-1, 1]
  * メッシュ = 4x4
  * 多項式次数 = 5
