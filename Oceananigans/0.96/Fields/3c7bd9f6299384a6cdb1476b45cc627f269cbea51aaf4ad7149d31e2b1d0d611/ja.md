```
Reduction(reduce!, operand; dims)
```

`reduce!`を使用して`operand`の`Reduction`を返します。ここで、`reduce!`は次のように呼び出すことができます。

```
reduce!(field, operand)
```

`dims`に沿って`operand`を減少させ、`field`に格納します。

# 例

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

# 出力
3×3 Matrix{Float64}:
 1.36111  2.25     3.36111
 2.25     3.36111  4.69444
 3.36111  4.69444  6.25
```
