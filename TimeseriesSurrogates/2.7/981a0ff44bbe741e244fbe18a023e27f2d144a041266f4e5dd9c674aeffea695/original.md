```
RandomCascade(paddingmode::String = "zeros")
```

A random cascade multifractal wavelet surrogate (Paluš, 2008)[^Paluš2008].

If the input signal length is not a power of 2, the signal must be  padded before the surrogate is constructed. `paddingmode` determines  how the signal is padded. Currently supported padding modes: `"zeros"`. The final surrogate (constructed from the padded signal) is subset to match the length of the original signal.

Random cascade surrogate preserve multifractal properties of the input  time series, that is, interactions among dyadic scales and nonlinear  dependencies[^Paluš2008].

[^Paluš2008]: Paluš, Milan (2008). Bootstrapping Multifractals: Surrogate Data from Random Cascades on Wavelet Dyadic Trees. Physical Review Letters, 101(13), 134101–. doi:10.1103/PhysRevLett.101.134101
