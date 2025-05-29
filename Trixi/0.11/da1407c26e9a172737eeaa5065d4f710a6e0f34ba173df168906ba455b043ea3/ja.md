```
IndicatorHennemannGassner(equations::AbstractEquations, basis;
                          alpha_max=0.5,
                          alpha_min=0.001,
                          alpha_smooth=true,
                          variable)
IndicatorHennemannGassner(semi::AbstractSemidiscretization;
                          alpha_max=0.5,
                          alpha_min=0.001,
                          alpha_smooth=true,
                          variable)
```

ショックキャプチャリング用のインジケーター（`equations` と `basis` を渡すとき）または適応メッシュリファインメント（AMR、`semi` を渡すとき）。

[`VolumeIntegralShockCapturingHG`](@ref) も参照してください。

## 参考文献

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
