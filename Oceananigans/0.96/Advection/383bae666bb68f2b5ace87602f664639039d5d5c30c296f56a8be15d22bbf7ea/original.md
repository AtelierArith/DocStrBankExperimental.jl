```
WENO([FT=Float64, FT2=Float32;]
     order = 5,
     grid = nothing,
     bounds = nothing)
```

Construct a weighted essentially non-oscillatory advection scheme of order `order` with precision `FT`.

# Arguments

  * `FT`: The floating point type used in the scheme. Default: `Oceananigans.defaults.FloatType`
  * `FT2`: The floating point type used in some performance-critical parts of the scheme. Default: `Float32`

# Keyword arguments

  * `order`: The order of the WENO advection scheme. Default: 5
  * `grid`: (defaults to `nothing`)

# Examples

```jldoctest
julia> using Oceananigans

julia> WENO()
WENO(order=5)
 Boundary scheme:
    └── WENO(order=3)
 Symmetric scheme:
    └── Centered(order=4)
```

```jldoctest
julia> using Oceananigans

julia> Nx, Nz = 16, 10;

julia> Lx, Lz = 1e4, 1e3;

julia> chebychev_spaced_z_faces(k) = - Lz/2 - Lz/2 * cos(π * (k - 1) / Nz);

julia> grid = RectilinearGrid(size = (Nx, Nz), halo = (4, 4), topology=(Periodic, Flat, Bounded),
                              x = (0, Lx), z = chebychev_spaced_z_faces);

julia> WENO(grid; order=7)
WENO(order=7)
 Boundary scheme:
    └── WENO(order=5)
 Symmetric scheme:
    └── Centered(order=6)
```
