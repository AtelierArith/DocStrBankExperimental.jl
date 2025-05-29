```
cube(xMin::Float64, yMin::Float64, zMin::Float64, xMax::Float64, yMax::Float64, zMax::Float64)::Solid
cube(center::Vector{Float64}, lx::Float64, ly::Float64, lz::Float64)::Solid
```

`xMin`、`yMin`、`zMin` および `xMax`、`yMax`、`zMax` を指定することで立方体を作成します。

または、`center` に位置する中心点と寸法 `lx`、`ly`、`lz` を使用して立方体を作成します。

# 例

```julia-repl
julia> cube(0, 0, 0, 1, 1, 1)
Main.SolidModeling.Solid(...)

julia> cube([0.5, 0.5, 0.5], 1, 1, 1)
Main.SolidModeling.Solid(...)
```
