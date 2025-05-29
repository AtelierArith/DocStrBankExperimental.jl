```
gun(::Type{T}, energy::Float64, width::Float64=1.0e-7, initial::Position=Position(0.0,0.0,-10.0), direction=Position(0.0,0.0,1.0)::T where {T <: Particle}
```

初期の `Particle` をランダム化されたガウス分布で構築するためのヘルパー。
