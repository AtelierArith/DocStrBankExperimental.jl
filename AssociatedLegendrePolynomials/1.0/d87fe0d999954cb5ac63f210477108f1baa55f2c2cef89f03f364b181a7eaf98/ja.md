```
struct LegendreOrthoNorm <: AbstractLegendreNorm end
```

関連するレジェンドル関数 $O_\ell^m(x)$ の直交正規化（完全）を示すトレイト型です。直交正規化は次のように定義されます。

$$
    \int_{-1}^{1} \left[ O_\ell^m(x) \right]^2 \,dx = 1
$$

標準（非正規化）レジェンドル関数 $P_\ell^m(x)$ に関する正規化係数（[`LegendreUnitNorm`](@ref)）は次のように与えられます。

$$
    O_\ell^m(x) \equiv \sqrt{\frac{2\ell+1}{2} \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
