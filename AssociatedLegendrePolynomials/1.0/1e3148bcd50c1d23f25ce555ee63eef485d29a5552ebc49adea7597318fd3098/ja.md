```
struct LegendreFourPiNorm <: AbstractLegendreNorm end
```

関連するレジェンドル関数 $F_\ell^m(x)$ の $4\pi$（測地学）正規化を示すトレイト型です。直交正規化は次のように定義されます。

$$
    \int_{-1}^{1} \left[ F_\ell^m(x) \right]^2 \,dx = 2
$$

標準（非正規化）レジェンドル関数 $P_\ell^m(x)$ に関する正規化因子（[`LegendreUnitNorm`](@ref)）は次のように与えられます。

$$
    F_\ell^m(x) \equiv \sqrt{2\pi(2\ell+1) \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
