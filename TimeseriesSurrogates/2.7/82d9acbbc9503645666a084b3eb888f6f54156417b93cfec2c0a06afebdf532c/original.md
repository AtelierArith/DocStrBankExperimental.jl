```
TAAFT(fϵ)
```

An truncated version of the amplitude-adjusted-fourier-transform surrogate[^Theiler1991][^Nakamura2006].

The truncation parameter and phase randomization procedure is identical to [`TFTS`](@ref), but here an additional step of rescaling back to the original data is performed. This preserves the amplitude distribution of the original data.

[^Theiler1991]: J. Theiler, S. Eubank, A. Longtin, B. Galdrikian, J. Farmer, Testing for nonlinearity in time series: The method of surrogate data, Physica D 58 (1–4) (1992) 77–94.

[^Nakamura2006]: Nakamura, Tomomichi, Michael Small, and Yoshito Hirata. "Testing for nonlinearity in irregular fluctuations with long-term trends." Physical Review E 74.2 (2006): 026205.
