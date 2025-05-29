```
lombscargle(times::AbstractVector{<:Real}, signal::AbstractVector{<:Real},
            [errors::AbstractVector{<:Real}]; keywords...)
```

`times`で観測された`signal`ベクトルのロムバ–スカーグル周期グラムを計算します。各信号点の不確実性を`errors`引数で指定することもできます。これらのベクトルはすべて同じ長さでなければなりません。

すべてのオプションのキーワードは、[`LombScargle.plan`](@ref)のドキュメントに記載されています。

信号に不確実性がある場合、`signal`ベクトルは`Measurement`オブジェクトのベクトル（[`Measurements.jl`](https://github.com/giordano/Measurements.jl)パッケージから）であることもでき、その場合は信号の不確実性のために別の`errors`ベクトルを渡す必要はありません。
