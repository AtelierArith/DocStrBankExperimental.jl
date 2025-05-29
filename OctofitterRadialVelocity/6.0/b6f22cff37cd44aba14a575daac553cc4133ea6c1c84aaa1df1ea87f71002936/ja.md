```
PlanetRelativeRVLikelihood(
    (;epoch=5000.0,  rv=−6.54, σ_rv=1.30),
    (;epoch=5050.1,  rv=−3.33, σ_rv=1.09),
    (;epoch=5100.2,  rv=7.90,  σ_rv=.11),

    jitter=:jitter_1,
    instrument_name="inst name",
)
```

これは、ホスト星と二次体との相対天体測定の尤度関数を表します。 `:epoch` (mjd)、 `:rv` (m/s)、および `:σ_rv` (m/s) はすべて必須です。

上記の例に加えて、Tables.jl 互換のソースを提供することができます。

`jitter` パラメータは、この機器のジッターのためにモデルから読み取るべき変数を指定します。
