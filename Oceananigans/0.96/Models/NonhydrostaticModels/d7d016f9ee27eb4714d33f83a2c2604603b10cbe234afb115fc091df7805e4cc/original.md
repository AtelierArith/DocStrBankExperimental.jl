```
set!(model::NonhydrostaticModel; enforce_incompressibility=true, kwargs...)
```

Set velocity and tracer fields of `model`. The keyword arguments `kwargs...` take the form `name=data`, where `name` refers to one of the fields of `model.velocities` or `model.tracers`, and the `data` may be an array, a function with arguments `(x, y, z)`, or any data type for which a `set!(ϕ::AbstractField, data)` function exists.

# Example

```julia
model = NonhydrostaticModel(grid=RectilinearGrid(size=(32, 32, 32), length=(1, 1, 1))

# Set u to a parabolic function of z, v to random numbers damped
# at top and bottom, and T to some silly array of half zeros,
# half random numbers.

u₀(x, y, z) = z / model.grid.Lz * (1 + z / model.grid.Lz)
v₀(x, y, z) = 1e-3 * rand() * u₀(x, y, z)

T₀ = rand(size(model.grid)...)
T₀[T₀ .< 0.5] .= 0

set!(model, u=u₀, v=v₀, T=T₀)
```
