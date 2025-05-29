```
fit!(m::QuantileRegression;
     verbose::Bool=false,
     quantile::Union{Nothing, AbstractFloat}=nothing,
     correct_leverage::Bool=false,
     kwargs...)
```

`QuantileRegression`の目的を最適化します。`verbose`が`true`の場合、各関数評価時に目的の値とパラメータがstdoutに印刷されます。

この関数は、`m`が正しく初期化されていることを前提としています。この関数は、モデルがすでにフィットされている場合は早期に戻ります。その場合は、`refit!`を呼び出してください。
