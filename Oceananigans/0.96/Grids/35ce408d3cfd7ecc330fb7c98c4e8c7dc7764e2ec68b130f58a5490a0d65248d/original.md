```
RectilinearGrid([architecture = CPU(), FT = Float64];
                size,
                x = nothing,
                y = nothing,
                z = nothing,
                halo = nothing,
                extent = nothing,
                topology = (Periodic, Periodic, Bounded))
```

Create a `RectilinearGrid` with `size = (Nx, Ny, Nz)` grid points.

# Positional arguments

  * `architecture`: Specifies whether arrays of coordinates and spacings are stored                 on the CPU or GPU. Default: `CPU()`.
  * `FT`: Floating point data type. Default: `Float64`.

# Keyword arguments

  * `size` (required): A tuple prescribing the number of grid points in non-`Flat` directions.                    `size` is a 3-tuple for 3D models, a 2-tuple for 2D models, and either a                    scalar or 1-tuple for 1D models.
  * `topology`: A 3-tuple `(TX, TY, TZ)` specifying the topology of the domain.             `TX`, `TY`, and `TZ` specify whether the `x`-, `y`-, and `z` directions are             `Periodic`, `Bounded`, or `Flat`. The topology `Flat` indicates that a model does             not vary in those directions so that derivatives and interpolation are zero.             The default is `topology = (Periodic, Periodic, Bounded)`.
  * `extent`: A tuple prescribing the physical extent of the grid in non-`Flat` directions, e.g.,           `(Lx, Ly, Lz)`. All directions are constructed with regular grid spacing and the domain           (in the case that no direction is `Flat`) is $0 ≤ x ≤ L_x$, $0 ≤ y ≤ L_y$, and           $-L_z ≤ z ≤ 0$, which is most appropriate for oceanic applications in which $z = 0$           usually is the ocean's surface.
  * `x`, `y`, and `z`: Each of `x, y, z` are either (i) 2-tuples that specify the end points of the domain                    in their respect directions (in which case scalar values may be used in `Flat`                    directions), or (ii) arrays or functions of the corresponding indices `i`, `j`, or `k`                    that specify the locations of cell faces in the `x`-, `y`-, or `z`-direction, respectively.                    For example, to prescribe the cell faces in `z` we need to provide a function that takes                    `k` as argument and returns the location of the faces for indices `k = 1` through `k = Nz + 1`,                    where `Nz` is the `size` of the stretched `z` dimension.

**Note**: *Either* `extent`, or *all* of `x`, `y`, and `z` must be specified.

  * `halo`: A tuple of integers that specifies the size of the halo region of cells surrounding         the physical interior for each non-`Flat` direction. The default is 3 halo cells in every direction.

The physical extent of the domain can be specified either via `x`, `y`, and `z` keyword arguments indicating the left and right endpoints of each dimensions, e.g., `x = (-π, π)` or via the `extent` argument, e.g., `extent = (Lx, Ly, Lz)`, which specifies the extent of each dimension in which case $0 ≤ x ≤ L_x$, $0 ≤ y ≤ L_y$, and $-L_z ≤ z ≤ 0$.

A grid topology may be specified via a tuple assigning one of `Periodic`, `Bounded`, and, `Flat` to each dimension. By default, a horizontally periodic grid topology `(Periodic, Periodic, Bounded)` is assumed.

Constants are stored using floating point values of type `FT`. By default this is `Float64`. Make sure to specify the desired `FT` if not using `Float64`.

# Grid properties

  * `(Nx, Ny, Nz) :: Int`: Number of physical points in the $(x, y, z)$-direction.
  * `(Hx, Hy, Hz) :: Int`: Number of halo points in the $(x, y, z)$-direction.
  * `(Lx, Ly, Lz) :: FT`: Physical extent of the grid in the $(x, y, z)$-direction.
  * `(Δxᶜᵃᵃ, Δyᵃᶜᵃ, Δzᵃᵃᶜ)`: Spacings in the $(x, y, z)$-directions between the cell faces.                          These are the lengths in $x$, $y$, and $z$ of `Center` cells and are                          defined at `Center` locations.
  * `(Δxᶠᵃᵃ, Δyᵃᶠᵃ, Δzᵃᵃᶠ)`: Spacings in the $(x, y, z)$-directions between the cell centers.                          These are the lengths in $x$, $y$, and $z$ of `Face` cells and are                          defined at `Face` locations.
  * `(xᶜᵃᵃ, yᵃᶜᵃ, zᵃᵃᶜ)`: $(x, y, z)$ coordinates of cell `Center`s.
  * `(xᶠᵃᵃ, yᵃᶠᵃ, zᵃᵃᶠ)`: $(x, y, z)$ coordinates of cell `Face`s.

# Examples

  * A grid with the default `Float64` type:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(32, 32, 32), extent=(1, 2, 3))
32×32×32 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 1.0)  regularly spaced with Δx=0.03125
├── Periodic y ∈ [0.0, 2.0)  regularly spaced with Δy=0.0625
└── Bounded  z ∈ [-3.0, 0.0] regularly spaced with Δz=0.09375
```

  * A grid with `Float32` type:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(Float32; size=(32, 32, 16), x=(0, 8), y=(-10, 10), z=(-π, π))
32×32×16 RectilinearGrid{Float32, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 8.0)          regularly spaced with Δx=0.25
├── Periodic y ∈ [-10.0, 10.0)       regularly spaced with Δy=0.625
└── Bounded  z ∈ [-3.14159, 3.14159] regularly spaced with Δz=0.392699
```

  * A two-dimenisional, horizontally-periodic grid:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(32, 32), extent=(2π, 4π), topology=(Periodic, Periodic, Flat))
32×32×1 RectilinearGrid{Float64, Periodic, Periodic, Flat} on CPU with 3×3×0 halo
├── Periodic x ∈ [3.60072e-17, 6.28319) regularly spaced with Δx=0.19635
├── Periodic y ∈ [7.20145e-17, 12.5664) regularly spaced with Δy=0.392699
└── Flat z
```

  * A one-dimensional "column" grid:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=256, z=(-128, 0), topology=(Flat, Flat, Bounded))
1×1×256 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── Flat x
├── Flat y
└── Bounded  z ∈ [-128.0, 0.0] regularly spaced with Δz=0.5
```

  * A horizontally-periodic regular grid with cell interfaces stretched hyperbolically near the top:

```jldoctest
julia> using Oceananigans

julia> σ = 1.1; # stretching factor

julia> Nz = 24; # vertical resolution

julia> Lz = 32; # depth (m)

julia> hyperbolically_spaced_faces(k) = - Lz * (1 - tanh(σ * (k - 1) / Nz) / tanh(σ));

julia> grid = RectilinearGrid(size = (32, 32, Nz),
                              x = (0, 64), y = (0, 64),
                              z = hyperbolically_spaced_faces)
32×32×24 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 64.0)   regularly spaced with Δx=2.0
├── Periodic y ∈ [0.0, 64.0)   regularly spaced with Δy=2.0
└── Bounded  z ∈ [-32.0, -0.0] variably spaced with min(Δz)=0.682695, max(Δz)=1.83091
```

  * A three-dimensional grid with regular spacing in $x$, cell interfaces at Chebyshev nodes in $y$, and cell interfaces hyperbolically stretched in $z$ near the top:

```jldoctest
julia> using Oceananigans

julia> Nx, Ny, Nz = 32, 30, 24;

julia> Lx, Ly, Lz = 200, 100, 32; # (m)

julia> chebychev_nodes(j) = - Ly/2 * cos(π * (j - 1) / Ny);

julia> σ = 1.1; # stretching factor

julia> hyperbolically_spaced_faces(k) = - Lz * (1 - tanh(σ * (k - 1) / Nz) / tanh(σ));

julia> grid = RectilinearGrid(size = (Nx, Ny, Nz),
                              topology = (Periodic, Bounded, Bounded),
                              x = (0, Lx),
                              y = chebychev_nodes,
                              z = hyperbolically_spaced_faces)
32×30×24 RectilinearGrid{Float64, Periodic, Bounded, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 200.0)  regularly spaced with Δx=6.25
├── Bounded  y ∈ [-50.0, 50.0] variably spaced with min(Δy)=0.273905, max(Δy)=5.22642
└── Bounded  z ∈ [-32.0, -0.0] variably spaced with min(Δz)=0.682695, max(Δz)=1.83091
```
