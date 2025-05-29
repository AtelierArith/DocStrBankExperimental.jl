```
DensityRatio(pr::PressureRatio, Isentropic[;gas=Air])
```

与えられた2点間の圧力比 `pr` を使用して、断熱的に接続された2点間の密度の比を計算します。断熱関係を使用します。

$$
\dfrac{\rho_2}{\rho_1} = \left(\dfrac{p_2}{p_1}\right)^{1/\gamma}
$$
