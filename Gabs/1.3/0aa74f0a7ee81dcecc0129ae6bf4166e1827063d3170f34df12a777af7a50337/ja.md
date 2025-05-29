```
fidelity(state1::GaussianState, state2::GaussianState; tol::Real = 128 * eps(1))
```

2つのガウス状態の結合フィデリティを計算します。定義は次のとおりです。

$$
F(\rho, \sigma) = Tr(\sqrt{\sqrt{\rho} \sigma \sqrt{\rho}}).
$$

参照: Banchi, Braunstein, and Pirandola, Phys. Rev. Lett. 115, 260501 (2015)

# 引数

  * `state1`, `state2`: 結合フィデリティを計算するガウス状態。
  * `tol`: $1$でのカットオフを超える許容誤差（含む）。
