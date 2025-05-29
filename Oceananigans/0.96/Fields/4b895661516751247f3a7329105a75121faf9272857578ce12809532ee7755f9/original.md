```
regrid!(a, b)
```

Regrid field `b` onto the grid of field `a`.

# Example

Generate a tracer field on a vertically stretched grid and regrid it on a regular grid.

```jldoctest
using Oceananigans

Nz, Lz = 2, 1.0
topology = (Flat, Flat, Bounded)

input_grid = RectilinearGrid(size=Nz, z = [0, Lz/3, Lz], topology=topology, halo=1)
input_field = CenterField(input_grid)
input_field[1, 1, 1:Nz] = [2, 3]

output_grid = RectilinearGrid(size=Nz, z=(0, Lz), topology=topology, halo=1)
output_field = CenterField(output_grid)

regrid!(output_field, input_field)

output_field[1, 1, :]

# output
4-element OffsetArray(::Vector{Float64}, 0:3) with eltype Float64 with indices 0:3:
 0.0
 2.333333333333333
 3.0
 0.0
```
