```
Accumulation(accumulate!, operand; dims)
```

Return a `Accumulation` of `operand` with `accumulate!`, where `accumulate!` can be called with

```
accumulate!(field, operand; dims)
```

to accumulate `operand` along `dims` and store in `field`.

# Example

```jldoctest
using Oceananigans

Nx, Ny, Nz = 3, 3, 3

grid = RectilinearGrid(size=(Nx, Ny, Nz), x=(0, 1), y=(0, 1), z=(0, 1),
                       topology=(Periodic, Periodic, Periodic))

c = CenterField(grid)

set!(c, (x, y, z) -> x + y + z)

cumsum_c² = Field(Accumulation(cumsum!, c^2, dims=3))

compute!(cumsum_c²)

cumsum_c²[1:Nx, 1:Ny, 1:Nz]

# output
3×3×3 Array{Float64, 3}:
[:, :, 1] =
 0.25      0.694444  1.36111
 0.694444  1.36111   2.25
 1.36111   2.25      3.36111

[:, :, 2] =
 0.944444  2.05556  3.61111
 2.05556   3.61111  5.61111
 3.61111   5.61111  8.05556

[:, :, 3] =
 2.30556   4.30556   6.97222
 4.30556   6.97222  10.3056
 6.97222  10.3056   14.3056
```
