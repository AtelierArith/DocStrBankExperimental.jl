```julia
condensation_force(p::ActinFriction.RingParams) -> Float64

```

リング内のLに対する凝縮力を計算します。

凝縮力は重なりの総数のみに依存するため、リングが収縮しても一定です。
