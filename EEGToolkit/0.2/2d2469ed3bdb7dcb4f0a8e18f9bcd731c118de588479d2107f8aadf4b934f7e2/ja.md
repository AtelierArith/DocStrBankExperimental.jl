`mean_band_power(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat)`

与えられた `Spectrogram` に対して、指定された周波数帯域 `[lower, upper]` の平均パワーを返します。この関数は実質的に次の計算を行います。

$$
\frac{1}{M\big(c_k - c_1\big)}\sum_{i=1}^{M}\sum_{j=c_1}^{c_k} S_{ij}
$$
