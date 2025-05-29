最小二乗スペクトル推定ツールボックス。

ヘルプについては、https://github.com/baggepinnen/LPVSpectral.jl の README.md を参照してください。

[Fredrik Bagge Carlson, Anders Robertsson, Rolf Johansson: "線形パラメータ変動スペクトル分解". In: 2017 American Control Conference 2017.](http://lup.lub.lu.se/record/ac32368e-e199-44ff-b76a-36668ac7d595) は、http://lup.lub.lu.se/record/ac32368e-e199-44ff-b76a-36668ac7d595 で入手可能です。

このモジュールは以下の関数を提供します。

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

および、DSP.jl から以下を再エクスポートします。

```
export periodogram, welch_pgram, Windows
```

Periodogram タイプと SpectralExt タイプは `plot(x::SpectralExt)` を使用してプロットできます。
