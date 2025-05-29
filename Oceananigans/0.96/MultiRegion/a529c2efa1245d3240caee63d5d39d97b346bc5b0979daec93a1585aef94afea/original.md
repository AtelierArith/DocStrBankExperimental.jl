```
ConformalCubedSphereGrid(arch=CPU(), FT=Float64;
                         panel_size,
                         z,
                         horizontal_direction_halo = 1,
                         z_halo = horizontal_direction_halo,
                         horizontal_topology = FullyConnected,
                         z_topology = Bounded,
                         radius = R_Earth,
                         non_uniform_conformal_mapping = false,
                         spacing_type = "geometric",
                         provided_conformal_mapping = nothing,
                         partition = CubedSpherePartition(; R = 1),
                         devices = nothing)
```

Return a `ConformalCubedSphereGrid` that comprises of six [`ConformalCubedSpherePanelGrid`](@ref)s; we refer to each of these grids as a "panel". Each panel corresponds to a face of the cube.

The keyword arguments prescribe the properties of each of the panels. Only the topology in the vertical direction can be prescribed and that's done via the `z_topology` keyword argument (default: `Bounded`). Topologies in both horizontal directions for a `ConformalCubedSphereGrid` are *always* [`FullyConnected`](@ref).

Halo size in both horizontal dimensions *must* be equal; this is prescribed via the `horizontal_halo :: Integer` keyword argument. The number of halo points in the $z$-direction is prescribed by the `z_halo :: Integer` keyword argument.

The connectivity between the `ConformalCubedSphereGrid` panels is depicted below.

```
                          +==========+==========+
                          ∥    ↑     ∥    ↑     ∥
                          ∥    1W    ∥    1S    ∥
                          ∥←3N P5 6W→∥←5E P6 2S→∥
                          ∥    4N    ∥    4E    ∥
                          ∥    ↓     ∥    ↓     ∥
               +==========+==========+==========+
               ∥    ↑     ∥    ↑     ∥
               ∥    5W    ∥    5S    ∥
               ∥←1N P3 4W→∥←3E P4 6S→∥
               ∥    2N    ∥    2E    ∥
               ∥    ↓     ∥    ↓     ∥
    +==========+==========+==========+
    ∥    ↑     ∥    ↑     ∥
    ∥    3W    ∥    3S    ∥
    ∥←5N P1 2W→∥←1E P2 4S→∥
    ∥    6N    ∥    6E    ∥
    ∥    ↓     ∥    ↓     ∥
    +==========+==========+
```

The North Pole of the sphere lies in the center of panel 3 (P3) and the South Pole in the center of panel 6 (P6).

The `partition` keyword argument prescribes the partitioning in regions within each panel; see [`CubedSpherePartition`](@ref). For example, a `CubedSpherePartition(; R=2)` implies that each of the panels are partitioned into 2 regions in each dimension; this adds up, e.g., to 24 regions for the  whole sphere. In the depiction below, the intra-panel `x, y` indices are depicted in the center of each region and the overall region index is shown at the bottom right of each region.

```
                                                +==========+==========+==========+==========+
                                                ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
                                                ∥          |          ∥          |          ∥
                                                ∥← (1, 2) →|← (2, 2) →∥← (1, 2) →|← (2, 2) →∥
                                                ∥          |          ∥          |          ∥
                                                ∥    ↓  19 |    ↓  20 ∥    ↓  23 |    ↓  24 ∥
                                                +-------- P 5 --------+-------- P 6 --------+
                                                ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
                                                ∥          |          ∥          |          ∥
                                                ∥← (1, 1) →|← (2, 1) →∥← (1, 1) →|← (2, 1) →∥
                                                ∥          |          ∥          |          ∥
                                                ∥    ↓  17 |    ↓  18 ∥    ↓  21 |    ↓  22 ∥
                          +==========+==========+==========+==========+==========+==========+
                          ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
                          ∥          |          ∥          |          ∥
                          ∥← (1, 2) →|← (2, 2) →∥← (1, 2) →|← (2, 2) →∥
                          ∥          |          ∥          |          ∥
                          ∥    ↓ 11  |    ↓  12 ∥    ↓  15 |    ↓  16 ∥
                          +-------- P 3 --------+-------- P 4 --------+
                          ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
                          ∥          |          ∥          |          ∥
                          ∥← (1, 1) →|← (2, 1) →∥← (1, 1) →|← (2, 1) →∥
                          ∥          |          ∥          |          ∥
                          ∥    ↓  9  |    ↓  10 ∥    ↓  13 |    ↓  14 ∥
    +==========+==========+==========+==========+==========+==========+
    ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
    ∥          |          ∥          |          ∥
    ∥← (1, 2) →|← (2, 2) →∥← (1, 2) →|← (2, 2) →∥
    ∥          |          ∥          |          ∥
    ∥    ↓   3 |    ↓   4 ∥    ↓   7 |    ↓   8 ∥
    +-------- P 1 --------+-------- P 2 --------+
    ∥    ↑     |    ↑     ∥    ↑     |    ↑     ∥
    ∥          |          ∥          |          ∥
    ∥← (1, 1) →|← (2, 1) →∥← (1, 1) →|← (2, 1) →∥
    ∥          |          ∥          |          ∥
    ∥    ↓   1 |    ↓   2 ∥    ↓   5 |    ↓   6 ∥
    +==========+==========+==========+==========+
```

Below, we show in detail panels 1 and 2 and the connectivity of each panel.

```
+===============+==============+==============+===============+
∥       ↑       |      ↑       ∥      ↑       |      ↑        ∥
∥      11W      |      9W      ∥      9S      |     10S       ∥
∥←19N (2, 1) 4W→|←3E (2, 2) 7W→∥←4E (2, 1) 8W→|←7E (2, 2) 13S→∥
∥       1N      |      2N      ∥      5N      |      6N       ∥
∥       ↓     3 |      ↓     4 ∥      ↓     7 |      ↓      8 ∥
+------------- P 1 ------------+------------ P 2 -------------+
∥       ↑       |      ↑       ∥      ↑       |      ↑        ∥
∥       3S      |      4S      ∥      7S      |      8S       ∥
∥←20N (1, 1) 2W→|←1E (2, 1) 5W→∥←2E (1, 1) 6W→|←5E (2, 1) 14S→∥
∥      23N      |     24N      ∥     24N      |     22N       ∥
∥       ↓     1 |      ↓     2 ∥      ↓     5 |      ↓      6 ∥
+===============+==============+==============+===============+
```

# Example

```jldoctest cubedspheregrid
julia> using Oceananigans

julia> using Oceananigans.MultiRegion: ConformalCubedSphereGrid

julia> grid = ConformalCubedSphereGrid(panel_size=(12, 12, 1), z=(-1, 0), radius=1)
ConformalCubedSphereGrid{Float64, Oceananigans.Grids.FullyConnected, Oceananigans.Grids.FullyConnected, Bounded} partitioned on CPU():
├── grids: 12×12×1 OrthogonalSphericalShellGrid{Float64, Oceananigans.Grids.FullyConnected, Oceananigans.Grids.FullyConnected, Bounded} on CPU with 3×3×3 halo and with precomputed metrics
├── partitioning: CubedSpherePartition with (1 region in each panel)
├── connectivity: CubedSphereConnectivity
└── devices: (CPU(), CPU(), CPU(), CPU(), CPU(), CPU())
```

The connectivities of the regions of our grid are stored in `grid.connectivity`. For example, to find out all connectivites on the South boundary of each region we call

```jldoctest cubedspheregrid
julia> using Oceananigans.MultiRegion: East, North, West, South

julia> for region in 1:length(grid); println(grid.connectivity.connections[region].south); end
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.North side, region 6
├── to:   Oceananigans.MultiRegion.South side, region 1
└── no rotation
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.East side, region 6
├── to:   Oceananigans.MultiRegion.South side, region 2
└── counter-clockwise rotation ↺
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.North side, region 2
├── to:   Oceananigans.MultiRegion.South side, region 3
└── no rotation
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.East side, region 2
├── to:   Oceananigans.MultiRegion.South side, region 4
└── counter-clockwise rotation ↺
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.North side, region 4
├── to:   Oceananigans.MultiRegion.South side, region 5
└── no rotation
CubedSphereRegionalConnectivity
├── from: Oceananigans.MultiRegion.East side, region 4
├── to:   Oceananigans.MultiRegion.South side, region 6
└── counter-clockwise rotation ↺
```
