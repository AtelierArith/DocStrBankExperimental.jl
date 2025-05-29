```julia
mdiff(
    mode::MomentMatching.EstimationMode,
    m::AbstractVector,
    momdat::AbstractVector,
    mmomdat::AbstractVector
) -> Any

```

モデルモーメントのデータモーメントからの偏差を計算します。[`EstimationMode`](@ref) の任意のサブタイプに対して定義されるべきです。

デフォルト：偏差は、各量のデータ平均で差を再スケーリングすることによって得られます。
