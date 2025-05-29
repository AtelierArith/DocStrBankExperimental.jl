StarAbsoluteRVLikelihood(         (;epoch=5000.0,  rv=−6.54, σ*rv=1.30),         (;epoch=5050.1,  rv=−3.33, σ*rv=1.09),         (;epoch=5100.2,  rv=7.90,  σ_rv=.11),

```
    offset=:offset_1,
    jitter=:jitter_1,
    instrument_name="inst name",

    # Optional:
    trend_function=(θ_system, epoch)->0.,
    gaussian_process=nothing
)
```

ホスト星と二次体の間の相対アストロメトリの尤度関数を表します。 `:epoch` (mjd)、`:rv` (m/s)、および `:σ_rv` (m/s) はすべて必須です。

`offset` および `jitter` パラメータは、この機器の RV ゼロポイントとジッターのためにモデルから読み取るべき変数を指定します。

上記の例に加えて、任意の Tables.jl 互換のソースを提供できます。
