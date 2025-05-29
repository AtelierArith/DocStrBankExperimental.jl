```
AutoRegressive(n, method = LPCLevinson())
```

Autoregressive surrogates of order-`n`. The autoregressive coefficients `φ` are estimated using `DSP.lpc(x, n, method)`, and thus see the documentation of DSP.jl for possible `method`s.

While these surrogates are obviously suited to test the null hypothesis whether the data are coming from a autoregressive process, the Fourier Transform-based surrogates are probably a better option. The current method is more like an explicit way to produce surrogates for the same hypothesis by fitting a model. It can be used as a convenient way to estimate autoregressive coefficients and automatically generate surrogates based on them.

The coefficients φ of the autoregressive fit can be found by doing

```julia
sg = surrogenerator(x, AutoRegressive(n))
φ = sg.init.φ
```
