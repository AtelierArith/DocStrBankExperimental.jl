```
rescale(x, from_min, from_max, to_min=0.0, to_max=1.0)
```

`x`を1つの線形スケール（`from_min`から`from_max`）から別のスケール（`to_min`から`to_max`）に変換します。

スケールはタプル形式でも指定できます：

```julia
rescale(x, (from_min, from_max), (to_min, to_max))
```

例

```julia
julia> rescale(15, 0, 100, 0, 1)
0.15

julia> rescale(15, (0, 100), (0, 1))
0.15

julia> rescale(pi/20, 0, 2pi, 0, 1)
0.025

julia> rescale(pi/20, (0, 2pi), (0, 1))
0.025

julia> rescale(25, 0, 1, 0, 1.609344)
40.2336

julia> rescale(15, (0, 100), (1000, 0))
850.0
```
