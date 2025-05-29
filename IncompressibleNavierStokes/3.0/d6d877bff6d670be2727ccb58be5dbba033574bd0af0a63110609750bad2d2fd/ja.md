```julia
get_scale_numbers(
    u,
    setup
) -> NamedTuple{(:uavg, :ϵ, :η, :λ, :Reλ, :L, :τ, :Re_int), <:NTuple{8, Any}}

```

次の次元スケール数を取得します [Pope2000](@cite):

  * 速度 $u_\text{avg} = \langle u_i u_i \rangle^{1/2}$
  * 減衰率 $\epsilon = 2 \nu \langle S_{ij} S_{ij} \rangle$
  * コルモゴロフ長スケール $\eta = (\frac{\nu^3}{\epsilon})^{1/4}$
  * テイラー長スケール $\lambda = (\frac{5 \nu}{\epsilon})^{1/2} u_\text{avg}$
  * テイラー・スケールのレイノルズ数 $Re_\lambda = \frac{\lambda u_\text{avg}}{\sqrt{3} \nu}$
  * 積分長スケール $L = \frac{3 \pi}{2 u_\text{avg}^2} \int_0^\infty \frac{E(k)}{k} \, \mathrm{d} k$
  * 大渦の回転時間 $\tau = \frac{L}{u_\text{avg}}$
