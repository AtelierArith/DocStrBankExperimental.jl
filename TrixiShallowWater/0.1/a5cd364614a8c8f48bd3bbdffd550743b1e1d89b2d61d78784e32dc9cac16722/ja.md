```
flux_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterMultiLayerEquations1D)
```

エントロピー保存分割形式で、静水圧は含まれていません。このフラックスは、エントロピー保存かつバランスの取れたスキームを作成するために、非保存的な [`flux_nonconservative_ersing_etal`](@ref) と一緒に使用する必要があります。

エントロピー安定な定式化を得るために、`surface_flux` を `FluxPlusDissipation(flux_ersing_etal, DissipationLocalLaxFriedrichs()), flux_nonconservative_ersing_etal` として設定できます。
