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

`LatitudeLongitudeGrid`を作成し、座標`(λ, φ, z)`はそれぞれ経度、緯度、および垂直座標を示します。

# 位置引数

  * `architecture`: 座標と間隔の配列がCPUまたはGPUに保存されるかどうかを指定します。デフォルト: `CPU()`.
  * `FT` : 浮動小数点データ型。デフォルト: `Float64`.

# キーワード引数

  * `size` (必須): 各方向のグリッドポイントの数を指定する3タプル。
  * `longitude` (必須), `latitude` (必須), `z` (デフォルト: `nothing`): 各引数は次のいずれかです:

    1. ドメインの端点を指定する2タプル、
    2. セルインターフェースの位置を指定する1次元配列、または
    3. インデックスを受け取り、セルインターフェースの位置を返す単一引数の関数。

    **注意**: 緯度と経度の座標の範囲は度数法であることが期待されます。
  * `radius`: グリッドが存在する球の半径。デフォルトは地球の半径と等しいです。
  * `topology`: 各方向のトポロジーのタプル（`Flat`, `Bounded`, `Periodic`）。垂直方向の`topology[3]`は`Bounded`でなければならず、緯度-経度のトポロジーは`Bounded`、`Periodic`、または`Flat`であることができます。トポロジーが提供されない場合、デフォルトでは、緯度の範囲が360度の場合はトポロジーは(`Periodic`, `Bounded`, `Bounded`)であり、それ以外の場合は(`Bounded`, `Bounded`, `Bounded`)です。
  * `precompute_metrics`: 水平間隔と面積を事前に計算するかどうかを指定するブール値。デフォルト: `true`。`false`の場合、水平方向の間隔と面積はシミュレーション中にオンザフライで計算されます。
  * `halo`: 物理的内部を囲むセルのハロ領域のサイズを指定する整数の3タプル。デフォルトはすべての方向に3つのハロセルです。

# 例

  * `Float64`型のデフォルトグリッド:

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

  * 上部付近でハイパーボリックに引き伸ばされたセルインターフェースを持つ有界球面セクター:

```jldoctest
julia> using Oceananigans

julia> σ = 1.1; # ストレッチングファクター

julia> Nz = 24; # 垂直解像度

julia> Lz = 1000; # 深さ (m)

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
