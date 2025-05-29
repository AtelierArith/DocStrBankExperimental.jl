```
LatitudeLongitudeGrid([architecture = CPU(), FT = Float64];
                      size,
                      longitude,
                      latitude,
                      z = nothing,
                      radius = R_Earth,
                      topology = nothing,
                      precompute_metrics = true,
                      halo = nothing)
```

Creates a `LatitudeLongitudeGrid` with coordinates `(λ, φ, z)` denoting longitude, latitude, and vertical coordinate respectively.

# Positional arguments

  * `architecture`: Specifies whether arrays of coordinates and spacings are stored                 on the CPU or GPU. Default: `CPU()`.
  * `FT` : Floating point data type. Default: `Float64`.

# Keyword arguments

  * `size` (required): A 3-tuple prescribing the number of grid points each direction.
  * `longitude` (required), `latitude` (required), `z` (default: `nothing`): Each is either a:

    1. 2-tuple that specify the end points of the domain,
    2. one-dimensional array specifying the cell interface locations, or
    3. a single-argument function that takes an index and returns cell interface location.

    **Note**: the latitude and longitude coordinates extents are expected in degrees.
  * `radius`: The radius of the sphere the grid lives on. By default is equal to the radius of Earth.
  * `topology`: Tuple of topologies (`Flat`, `Bounded`, `Periodic`) for each direction. The vertical             `topology[3]` must be `Bounded`, while the latitude-longitude topologies can be             `Bounded`, `Periodic`, or `Flat`. If no topology is provided then, by default, the             topology is (`Periodic`, `Bounded`, `Bounded`) if the latitudinal extent is 360 degrees             or (`Bounded`, `Bounded`, `Bounded`) otherwise.
  * `precompute_metrics`: Boolean specifying whether to precompute horizontal spacings and areas.                       Default: `true`. When `false`, horizontal spacings and areas are computed                       on-the-fly during a simulation.
  * `halo`: A 3-tuple of integers specifying the size of the halo region of cells surrounding         the physical interior. The default is 3 halo cells in every direction.

# Examples

  * A default grid with `Float64` type:

```jldoctest
julia> using Oceananigans

julia> grid = LatitudeLongitudeGrid(size=(36, 34, 25),
                                    longitude = (-180, 180),
                                    latitude = (-85, 85),
                                    z = (-1000, 0))
36×34×25 LatitudeLongitudeGrid{Float64, Periodic, Bounded, Bounded} on CPU with 3×3×3 halo and with precomputed metrics
├── longitude: Periodic λ ∈ [-180.0, 180.0) regularly spaced with Δλ=10.0
├── latitude:  Bounded  φ ∈ [-85.0, 85.0]   regularly spaced with Δφ=5.0
└── z:         Bounded  z ∈ [-1000.0, 0.0]  regularly spaced with Δz=40.0
```

  * A bounded spherical sector with cell interfaces stretched hyperbolically near the top:

```jldoctest
julia> using Oceananigans

julia> σ = 1.1; # stretching factor

julia> Nz = 24; # vertical resolution

julia> Lz = 1000; # depth (m)

julia> hyperbolically_spaced_faces(k) = - Lz * (1 - tanh(σ * (k - 1) / Nz) / tanh(σ));

julia> grid = LatitudeLongitudeGrid(size=(36, 34, Nz),
                                    longitude = (-180, 180),
                                    latitude = (-20, 20),
                                    z = hyperbolically_spaced_faces,
                                    topology = (Bounded, Bounded, Bounded))
36×34×24 LatitudeLongitudeGrid{Float64, Bounded, Bounded, Bounded} on CPU with 3×3×3 halo and with precomputed metrics
├── longitude: Bounded  λ ∈ [-180.0, 180.0] regularly spaced with Δλ=10.0
├── latitude:  Bounded  φ ∈ [-20.0, 20.0]   regularly spaced with Δφ=1.17647
└── z:         Bounded  z ∈ [-1000.0, -0.0] variably spaced with min(Δz)=21.3342, max(Δz)=57.2159
```
