```
gravity(ϕ,P::Planet)
```

惑星の表面での測地緯度 `ϕ` における合計 `gravity` を計算します (m⋅s⁻²)。

```Julia
julia> gravity(0,Earth)
9.780325333855085

julia> gravity(π/2,Earth)
9.832184939227085
```
