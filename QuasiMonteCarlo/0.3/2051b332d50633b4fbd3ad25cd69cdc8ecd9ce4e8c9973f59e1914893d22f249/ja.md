```julia
DigitalShift <: ScrambleMethod
```

デジタルシフト。 `randomize(x, R::DigitalShift)` は `x` のスクランブルされたバージョンを返します。

スクランブルメソッドはデジタルシフトです。各座標を基数 `b` でスクランブルします。すなわち、`yₖ = (xₖ + Uₖ) mod b` であり、`Uₖ ∼ 𝕌({0:b-1})` です。`U` はすべての点 `points` に対して同じですが、各次元に沿って独立同分布です。
