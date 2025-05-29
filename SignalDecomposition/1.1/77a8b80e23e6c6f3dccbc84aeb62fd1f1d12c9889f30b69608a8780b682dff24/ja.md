```
Sinusoidal(fs)
```

時系列 `s` を **和** `x + r` に分解します。ここで `x` は与えられた周波数 `fs` の正弦波成分であり、係数 $A, \phi$ を最小化する表現

$$
s \approx A_0 + \sum_i A_i \cos(2\pi f_i t + \phi_i)
$$

において $A_0 = \bar{s}$ は平均です。

この方法は、パッケージ [LPVSpectral.jl](https://github.com/baggepinnen/LPVSpectral.jl) を使用した周波数領域での新しい最小二乗アルゴリズムを利用しています[^Bagge2017]。これは非等間隔の `t` 軸（および通常のもの）でも機能し、一般的に非常に正確ですが、性能スケーリングは O(N^2.4) であり、[`Fourier`](@ref) の O(n log(n)) とは異なります。

任意の信号長で機能するため、この方法は常にゼロ周波数のフーリエ成分を推定し、それを `x` に帰属させます。フィッティングされた係数 $A, \phi$ は構造体のフィールド `.A` と `.φ` として利用可能です（最初のエントリはゼロ周波数成分 $A_0, \phi_0$ です）。

[^Bagge2017]: F. Bagge Carlson et al., [Linear Parameter-Varying Spectral Decomposition](https://lup.lub.lu.se/search/publication/ac32368e-e199-44ff-b76a-36668ac7d595).
