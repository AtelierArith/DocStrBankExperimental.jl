```
fit!(m::RobustLinearModel; initial_scale::Union{Symbol, Real}=:mad,
          σ0::Union{Nothing, Symbol, Real}=initial_scale,
          initial_coef::AbstractVector=[],
          β0::AbstractVector=initial_coef,
          correct_leverage::Bool=false, kwargs...)
```

`RobustLinearModel`の目的関数を最適化します。`verbose`が`true`の場合、各イテレーションで目的関数の値とパラメータが標準出力に印刷されます。

この関数は、`m`が正しく初期化されていることを前提としています。

この関数は、モデルがすでにフィットされている場合は早期に戻ります。その場合は、`refit!`を呼び出してください。
