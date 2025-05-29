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

`size = (Nx, Ny, Nz)` グリッドポイントを持つ `RectilinearGrid` を作成します。

# 位置引数

  * `architecture`: 座標と間隔の配列が CPU または GPU に保存されるかを指定します。デフォルト: `CPU()`.
  * `FT`: 浮動小数点データ型。デフォルト: `Float64`.

# キーワード引数

  * `size` (必須): 非 `Flat` 方向のグリッドポイントの数を指定するタプルです。`size` は 3D モデルの場合は 3 タプル、2D モデルの場合は 2 タプル、1D モデルの場合はスカラーまたは 1 タプルです。
  * `topology`: ドメインのトポロジーを指定する 3 タプル `(TX, TY, TZ)` です。`TX`, `TY`, `TZ` はそれぞれ `x`-, `y`-, `z` 方向が `Periodic`, `Bounded`, または `Flat` であるかを指定します。トポロジー `Flat` は、モデルがそれらの方向で変化しないことを示し、導関数と補間がゼロであることを意味します。デフォルトは `topology = (Periodic, Periodic, Bounded)` です。
  * `extent`: 非 `Flat` 方向のグリッドの物理的な範囲を指定するタプルです。例: `(Lx, Ly, Lz)`。すべての方向は規則的なグリッド間隔で構成され、ドメイン（どの方向も `Flat` でない場合）は $0 ≤ x ≤ L_x$, $0 ≤ y ≤ L_y$, $-L_z ≤ z ≤ 0$ であり、通常 $z = 0$ が海面である海洋アプリケーションに最も適しています。
  * `x`, `y`, `z`: 各 `x, y, z` は (i) ドメインの端点をそれぞれの方向で指定する 2 タプル（この場合、`Flat` 方向ではスカラー値を使用できます）または (ii) 対応するインデックス `i`, `j`, `k` の配列または関数であり、それぞれ `x`-, `y`-, `z`-方向のセル面の位置を指定します。例えば、`z` のセル面を指定するには、`k` を引数として受け取り、インデックス `k = 1` から `k = Nz + 1` までの面の位置を返す関数を提供する必要があります。ここで `Nz` は伸ばされた `z` 次元の `size` です。

**注意**: `extent` または `x`, `y`, `z` の *すべて* を指定する必要があります。

  * `halo`: 物理的内部を囲むセルのハロー領域のサイズを指定する整数のタプルです。デフォルトはすべての方向に 3 つのハロセルです。

ドメインの物理的な範囲は、各次元の左端と右端を示す `x`, `y`, `z` キーワード引数を介して指定することも、`extent` 引数を介して指定することもできます。例: `x = (-π, π)` または `extent = (Lx, Ly, Lz)` の場合、$0 ≤ x ≤ L_x$, $0 ≤ y ≤ L_y$, $-L_z ≤ z ≤ 0$ となります。

グリッドのトポロジーは、各次元に `Periodic`, `Bounded`, `Flat` のいずれかを割り当てるタプルを介して指定できます。デフォルトでは、水平周期的グリッドトポロジー `(Periodic, Periodic, Bounded)` が仮定されます。

定数は `FT` 型の浮動小数点値を使用して保存されます。デフォルトは `Float64` です。`Float64` を使用しない場合は、希望する `FT` を指定してください。

# グリッドのプロパティ

  * `(Nx, Ny, Nz) :: Int`: $(x, y, z)$ 方向の物理ポイントの数。
  * `(Hx, Hy, Hz) :: Int`: $(x, y, z)$ 方向のハロポイントの数。
  * `(Lx, Ly, Lz) :: FT`: $(x, y, z)$ 方向のグリッドの物理的範囲。
  * `(Δxᶜᵃᵃ, Δyᵃᶜᵃ, Δzᵃᵃᶜ)`: セル面間の $(x, y, z)$ 方向の間隔。これらは `Center` セルの $x$, $y$, $z$ の長さであり、`Center` の位置で定義されています。
  * `(Δxᶠᵃᵃ, Δyᵃᶠᵃ, Δzᵃᵃᶠ)`: セル中心間の $(x, y, z)$ 方向の間隔。これらは `Face` セルの $x$, $y$, $z$ の長さであり、`Face` の位置で定義されています。
  * `(xᶜᵃᵃ, yᵃᶜᵃ, zᵃᵃᶜ)`: セル `Center` の $(x, y, z)$ 座標。
  * `(xᶠᵃᵃ, yᵃᶠᵃ, zᵃᵃᶠ)`: セル `Face` の $(x, y, z)$ 座標。

# 例

  * デフォルトの `Float64` 型のグリッド:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(32, 32, 32), extent=(1, 2, 3))
32×32×32 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 1.0)  regularly spaced with Δx=0.03125
├── Periodic y ∈ [0.0, 2.0)  regularly spaced with Δy=0.0625
└── Bounded  z ∈ [-3.0, 0.0] regularly spaced with Δz=0.09375
```

  * `Float32` 型のグリッド:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(Float32; size=(32, 32, 16), x=(0, 8), y=(-10, 10), z=(-π, π))
32×32×16 RectilinearGrid{Float32, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 8.0)          regularly spaced with Δx=0.25
├── Periodic y ∈ [-10.0, 10.0)       regularly spaced with Δy=0.625
└── Bounded  z ∈ [-3.14159, 3.14159] regularly spaced with Δz=0.392699
```

  * 二次元の水平周期的グリッド:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(32, 32), extent=(2π, 4π), topology=(Periodic, Periodic, Flat))
32×32×1 RectilinearGrid{Float64, Periodic, Periodic, Flat} on CPU with 3×3×0 halo
├── Periodic x ∈ [3.60072e-17, 6.28319) regularly spaced with Δx=0.19635
├── Periodic y ∈ [7.20145e-17, 12.5664) regularly spaced with Δy=0.392699
└── Flat z
```

  * 一次元の「カラム」グリッド:

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=256, z=(-128, 0), topology=(Flat, Flat, Bounded))
1×1×256 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── Flat x
├── Flat y
└── Bounded  z ∈ [-128.0, 0.0] regularly spaced with Δz=0.5
```

  * 上部付近でハイパーボリックに伸ばされたセルインターフェースを持つ水平周期的な正規グリッド:

```jldoctest
julia> using Oceananigans

julia> σ = 1.1; # 伸ばし係数

julia> Nz = 24; # 垂直解像度

julia> Lz = 32; # 深さ (m)

julia> hyperbolically_spaced_faces(k) = - Lz * (1 - tanh(σ * (k - 1) / Nz) / tanh(σ));

julia> grid = RectilinearGrid(size = (32, 32, Nz),
                              x = (0, 64), y = (0, 64),
                              z = hyperbolically_spaced_faces)
32×32×24 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 64.0)   regularly spaced with Δx=2.0
├── Periodic y ∈ [0.0, 64.0)   regularly spaced with Δy=2.0
└── Bounded  z ∈ [-32.0, -0.0] variably spaced with min(Δz)=0.682695, max(Δz)=1.83091
```

  * $$
    x
    $$

    方向で規則的な間隔、$y$ 方向でチェビシェフノードにセルインターフェース、$z$ 方向で上部付近にハイパーボリックに伸ばされたセルインターフェースを持つ三次元グリッド:

```jldoctest
julia> using Oceananigans

julia> Nx, Ny, Nz = 32, 30, 24;

julia> Lx, Ly, Lz = 200, 100, 32; # (m)

julia> chebychev_nodes(j) = - Ly/2 * cos(π * (j - 1) / Ny);

julia> σ = 1.1; # 伸ばし係数

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
