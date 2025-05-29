```julia
artscene_filter(
    raw_image::Array{T<:AbstractFloat, 3}
) -> Tuple{Array{Float64, 4}, Array{Float64, 3}}

```

# 概要

画像に対してフルアートシーンフィルターツールチェーンを処理します。

# 引数

  * `raw_image::Array{Real, 3}`: ARTSCENEフィルタで処理する生のRGB画像。

# メソッドリスト / 定義場所

```julia
artscene_filter(raw_image)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/ARTSCENE.jl:294`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/ARTSCENE.jl)で定義されています。
