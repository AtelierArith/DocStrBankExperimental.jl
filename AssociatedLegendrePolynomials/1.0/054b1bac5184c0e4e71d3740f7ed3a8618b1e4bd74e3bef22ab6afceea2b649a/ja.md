```
struct LegendreUnitNorm <: AbstractLegendreNorm end
```

非正規化された関連レジェンドル関数 $P_\ell^m(x)$ を示すトレイト型で、これは球面座標におけるラプラス方程式のコラティチュード $\theta$ 部分を解きます。ここで $x=\cos(\theta)$ です。次数 $\ell=0$、順序 $m=0$ の定数関数は、単位に正規化されています：

$$
    P_0^0(x) = 1
$$
