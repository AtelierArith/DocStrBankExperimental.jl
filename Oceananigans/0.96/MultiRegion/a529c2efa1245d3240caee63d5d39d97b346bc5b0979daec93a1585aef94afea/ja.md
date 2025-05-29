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

`ConformalCubedSphereGrid`を返します。これは6つの[`ConformalCubedSpherePanelGrid`](@ref)で構成されており、これらのグリッドを「パネル」と呼びます。各パネルは立方体の面に対応しています。

キーワード引数は各パネルの特性を指定します。垂直方向のトポロジーのみが指定可能で、これは`z_topology`キーワード引数を介して行われます（デフォルト：`Bounded`）。`ConformalCubedSphereGrid`の両方の水平方向のトポロジーは*常に*[`FullyConnected`](@ref)です。

両方の水平方向のハロサイズは*等しく*なければなりません。これは`horizontal_halo :: Integer`キーワード引数を介して指定されます。$z$方向のハロポイントの数は`z_halo :: Integer`キーワード引数によって指定されます。

`ConformalCubedSphereGrid`パネル間の接続性は以下に示されています。

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

球の北極はパネル3（P3）の中心にあり、南極はパネル6（P6）の中心にあります。

`partition`キーワード引数は各パネル内の領域の分割を指定します。詳細は[`CubedSpherePartition`](@ref)を参照してください。たとえば、`CubedSpherePartition(; R=2)`は、各パネルが各次元で2つの領域に分割されることを意味します。これは、全体の球体に対して24の領域に合計されます。以下の図では、パネル内の`x, y`インデックスが各領域の中央に示され、全体の領域インデックスが各領域の右下に示されています。

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

以下に、パネル1と2の詳細と各パネルの接続性を示します。

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

# 例

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

グリッドの領域の接続性は`grid.connectivity`に保存されています。たとえば、各領域の南境界のすべての接続性を見つけるには、次のようにします。

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
