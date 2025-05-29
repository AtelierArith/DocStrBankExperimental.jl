```
flux_chan_etal(u_ll, u_rr, orientation,
               equations::ShallowWaterEquationsQuasi1D)
```

全エネルギー保存（準1D浅水方程式の数学的エントロピー）分割形式。底面の地形がゼロでない場合、このスキームは`volume_flux`として使用されるときに良好にバランスが取れます。`surface_flux`は、例えば、[`FluxPlusDissipation(flux_chan_etal, DissipationLocalLaxFriedrichs())`](@ref)を使用する必要があります。

さらなる詳細は、以下の論文にあります：

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)  高次エントロピー安定スキームの準1次元浅水方程式および圧縮可能なオイラー方程式 [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
