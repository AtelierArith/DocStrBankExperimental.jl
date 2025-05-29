```
struct LegendreSphereNorm <: AbstractLegendreNorm end
```

関連するレジェンドル関数 $\lambda_\ell^m(x)$ の球面調和正規化を示すトレイト型です。球面調和正規化は次のように定義されます。

$$
    \int_{-1}^{1} \left[ \lambda_\ell^m(x) \right]^2 \,dx = \frac{1}{2\pi}
$$

標準（正規化されていない）レジェンドル関数 $P_\ell^m(x)$ に関する正規化因子（[`LegendreUnitNorm`](@ref)）は次のように与えられます。

$$
    \lambda_\ell^m(x) \equiv \sqrt{\frac{2\ell+1}{4\pi} \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
