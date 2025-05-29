```
MarginalizedStarAbsoluteRVLikelihood(
    (;epoch=5000.0,  rv=−6.54, σ_rv=1.30),
    (;epoch=5050.1,  rv=−3.33, σ_rv=1.09),
    (;epoch=5100.2,  rv=7.90,  σ_rv=.11),

    jitter=:jitter_1,
    instrument_name="inst name",
)
```

これは、ホスト星と二次体との相対天体測定の尤度関数を表します。 `:epoch` (mjd)、 `:rv` (m/s)、および `:σ_rv` (m/s) はすべて必須です。上記の例に加えて、任意のTables.jl互換のソースを提供できます。

`jitter` パラメータは、この機器のジッターのためにモデルから読み取るべき変数を指定します。

`StarAbsoluteRVLikelihood`とは異なり、このバージョンは機器のRVゼロポイントに対して解析的に周辺化します。これにより、ほとんどの場合で高速化されます。ただし、RVゼロポイントに適用したい特定の事前分布、ゼロポイント間の相関、階層モデルなどがある場合は、`StarAbsoluteRVLikelihood`を使用する必要があります。

さらに、解析的周辺化ではガウスフィットおよびトレンドフィットはサポートされていません。
