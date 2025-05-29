Least-squares spectral estimation toolbox.

For help, see README.md at https://github.com/baggepinnen/LPVSpectral.jl and

[Fredrik Bagge Carlson, Anders Robertsson, Rolf Johansson: "Linear Parameter-Varying Spectral Decomposition". In: 2017 American Control Conference 2017.](http://lup.lub.lu.se/record/ac32368e-e199-44ff-b76a-36668ac7d595) Available at: http://lup.lub.lu.se/record/ac32368e-e199-44ff-b76a-36668ac7d595

This module provide the functions

```
ls_spectral
tls_spectral
ls_windowpsd
ls_windowcsd
ls_cohere
ls_spectral_lpv
ls_sparse_spectral_lpv
ls_windowpsd_lpv
basis_activation_func
```

and re-exports the following from DSP.jl

```
export periodogram, welch_pgram, Windows
```

Periodogram types and SpectralExt type can be plotted using `plot(x::SpectralExt)`
