```
white_noise!(ρ::AbstractMatrix, v::Real)
```

`ρ`をその場で修正し、`v * rho + (1 - v) * id`に変換します。ここで、`id`は最大混合状態です。
