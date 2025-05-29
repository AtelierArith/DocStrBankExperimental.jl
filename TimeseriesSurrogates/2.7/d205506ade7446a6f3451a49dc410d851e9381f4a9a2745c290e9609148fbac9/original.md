```
RandomFourier(phases = true)
```

A surrogate that randomizes the Fourier components of the signal in some manner. If `phases==true`, the phases are randomized, otherwise the amplitudes are randomized. `FT` is an alias for `RandomFourier`.

Random Fourier phase surrogates[^Theiler1991] preserve the autocorrelation function, or power spectrum, of the original signal. Random Fourier amplitude surrogates preserve the mean and autocorrelation function but do not preserve the variance of the original. Random amplitude surrogates are not common in the literature, but are provided for convenience.

Random phase surrogates can be used to test the null hypothesis that the original signal was produced by a linear Gaussian process [^Theiler1991].

[^Theiler1991]: J. Theiler, S. Eubank, A. Longtin, B. Galdrikian, J. Farmer, Testing for nonlinearity in time series: The method of surrogate data, Physica D 58 (1–4) (1992) 77–94.
