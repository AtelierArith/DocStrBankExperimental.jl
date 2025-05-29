```
KernelFunctionOperation{LX, LY, LZ}(kernel_function, grid, arguments...)
```

Construct a `KernelFunctionOperation` at location `(LX, LY, LZ)` on `grid` with `arguments`.

`kernel_function` is called with

```julia
kernel_function(i, j, k, grid, arguments...)
```

Note that `compute!(kfo::KernelFunctionOperation)` calls `compute!` on all `kfo.arguments`.

# Examples

Construct a `KernelFunctionOperation` that returns random numbers:

```jldoctest kfo
using Oceananigans

grid = RectilinearGrid(size=(1, 8, 8), extent=(1, 1, 1));

random_kernel_function(i, j, k, grid) = rand(); # use CUDA.rand on the GPU

kernel_op = KernelFunctionOperation{Center, Center, Center}(random_kernel_function, grid)

# output

KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── kernel_function: random_kernel_function (generic function with 1 method)
└── arguments: ()
```

Construct a `KernelFunctionOperation` using the vertical vorticity operator used internally to compute vertical vorticity on all grids:

```jldoctest kfo
using Oceananigans.Operators: ζ₃ᶠᶠᶜ # called with signature ζ₃ᶠᶠᶜ(i, j, k, grid, u, v)

model = HydrostaticFreeSurfaceModel(; grid);

u, v, w = model.velocities;

ζ_op = KernelFunctionOperation{Face, Face, Center}(ζ₃ᶠᶠᶜ, grid, u, v)

# output

KernelFunctionOperation at (Face, Face, Center)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── kernel_function: ζ₃ᶠᶠᶜ (generic function with 1 method)
└── arguments: ("1×8×8 Field{Face, Center, Center} on RectilinearGrid on CPU", "1×8×8 Field{Center, Face, Center} on RectilinearGrid on CPU")
```
