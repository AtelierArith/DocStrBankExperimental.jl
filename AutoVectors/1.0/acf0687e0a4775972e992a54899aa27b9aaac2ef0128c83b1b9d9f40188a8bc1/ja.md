ifftav(F::AutoVector{ComplexF64},freqspacing,maxind)

周波数間隔freqspacingで均一な周波数グリッド上に定義された関数F_iに対して、逆フーリエ変換を返します。

$$
f(x) = \frac{1}{\sqrt{2 \pi}} \int dk e^{i k x} F(k)
$$
