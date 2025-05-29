`mean_band_power(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat)`

Given a `Spectrogram`, returns the mean power in a given frequency band `[lower, upper]`. This function  effectively computes 

$$
\frac{1}{M\big(c_k - c_1\big)}\sum_{i=1}^{M}\sum_{j=c_1}^{c_k} S_{ij}
$$
