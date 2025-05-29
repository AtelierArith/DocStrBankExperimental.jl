```
LazyNBProportionalBandSpectrum{NO,IsTonal,TF,TAmp,TBandsC}
```

オクターブ分数 `NO` と `eltype` `TF` から構成された狭帯域（`NB`）スペクトルを持つ比例バンドスペクトルの遅延表現です。

`IsTonal` は、音響エネルギーが狭い周波数帯域を通じてどのように分配されるかを示します：

  * `IsTonal == false` は、音響エネルギーが各バンド全体に均等に分配されると仮定されることを意味します
  * `IsTonal == true` は、音響エネルギーが各バンドの中心に集中していると仮定されることを意味します
