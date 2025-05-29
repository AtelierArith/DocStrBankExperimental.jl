```
cube(xMin::Float64, yMin::Float64, zMin::Float64, xMax::Float64, yMax::Float64, zMax::Float64)::Solid
cube(center::Vector{Float64}, lx::Float64, ly::Float64, lz::Float64)::Solid
```

Creates a cube by specifying its bounding box `xMin`, `yMin`, `zMin` and `xMax`, `yMax`, `zMax`.

Or create a cube using a center point located in `center` and dimensions `lx`, `ly`, and `lz`.

# Examples

```julia-repl
julia> cube(0, 0, 0, 1, 1, 1)
Main.SolidModeling.Solid(...)

julia> cube([0.5, 0.5, 0.5], 1, 1, 1)
Main.SolidModeling.Solid(...)
```
