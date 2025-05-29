```
Reduction(reduce!, operand; dims)
```

Return a `Reduction` of `operand` with `reduce!`, where `reduce!` can be called with

```
reduce!(field, operand)
```

to reduce `operand` along `dims` and store in `field`.

# Example

```jldoctest
using Oceananigans

Nx, Ny, Nz = 3, 3, 3

grid = RectilinearGrid(size=(Nx, Ny, Nz), x=(0, 1), y=(0, 1), z=(0, 1),
                       topology=(Periodic, Periodic, Periodic))

c = CenterField(grid)

set!(c, (x, y, z) -> x + y + z)

max_c² = Field(Reduction(maximum!, c^2, dims=3))

compute!(max_c²)

max_c²[1:Nx, 1:Ny]

# output
3×3 Matrix{Float64}:
 1.36111  2.25     3.36111
 2.25     3.36111  4.69444
 3.36111  4.69444  6.25
```
