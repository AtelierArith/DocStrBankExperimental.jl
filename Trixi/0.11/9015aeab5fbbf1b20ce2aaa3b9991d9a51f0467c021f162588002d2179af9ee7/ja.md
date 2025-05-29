```
VolumeIntegralShockCapturingHG(indicator; volume_flux_dg=flux_central,
                                          volume_flux_fv=flux_lax_friedrichs)
```

DG法のためのショックキャプチャリング体積積分タイプで、数値フラックス`volume_flux_fv`を用いた有限体積法の凸ブレンドと[`VolumeIntegralFluxDifferencing`](@ref)の体積フラックス`volume_flux_dg`を使用します。ブレンドの量は`indicator`によって決定されます。例えば、[`IndicatorHennemannGassner`](@ref)です。

## 参考文献

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
