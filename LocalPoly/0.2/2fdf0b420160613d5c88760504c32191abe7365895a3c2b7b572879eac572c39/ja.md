```julia
plugin_bandwidth(
    x::AbstractArray{T<:Real, 1},
    y::AbstractArray{T<:Real, 1};
    ν,
    p,
    kernel,
    W
) -> Any

```

ルールオブサムプラグインバンド幅を推定します。
