```
KernelFunctionOperation{LX, LY, LZ}(kernel_function, grid, arguments...)
```

位置 `(LX, LY, LZ)` の `grid` 上に `arguments` を持つ `KernelFunctionOperation` を構築します。

`kernel_function` は次のように呼び出されます。

```julia
kernel_function(i, j, k, grid, arguments...)
```

`compute!(kfo::KernelFunctionOperation)` はすべての `kfo.arguments` に対して `compute!` を呼び出すことに注意してください。

# 例

ランダムな数値を返す `KernelFunctionOperation` を構築します。

```jldoctest kfo
using Oceananigans

grid = RectilinearGrid(size=(1, 8, 8), extent=(1, 1, 1));

random_kernel_function(i, j, k, grid) = rand(); # GPU上でCUDA.randを使用

kernel_op = KernelFunctionOperation{Center, Center, Center}(random_kernel_function, grid)

# 出力

KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── kernel_function: random_kernel_function (generic function with 1 method)
└── arguments: ()
```

すべてのグリッドで垂直渦度を計算するために内部で使用される垂直渦度演算子を使用して `KernelFunctionOperation` を構築します。

```jldoctest kfo
using Oceananigans.Operators: ζ₃ᶠᶠᶜ # シグネチャ ζ₃ᶠᶠᶜ(i, j, k, grid, u, v) で呼び出される

model = HydrostaticFreeSurfaceModel(; grid);

u, v, w = model.velocities;

ζ_op = KernelFunctionOperation{Face, Face, Center}(ζ₃ᶠᶠᶜ, grid, u, v)

# 出力

KernelFunctionOperation at (Face, Face, Center)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── kernel_function: ζ₃ᶠᶠᶜ (generic function with 1 method)
└── arguments: ("1×8×8 Field{Face, Center, Center} on RectilinearGrid on CPU", "1×8×8 Field{Center, Face, Center} on RectilinearGrid on CPU")
```
