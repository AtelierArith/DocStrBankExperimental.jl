```
Grid = create_CartGrid(; size=(), x = nothing, z = nothing, y = nothing, extent = nothing, CharDim = nothing)
```

指定されたサイズの1D、2D、または3D直交グリッドを作成します。グリッドは、サイズを定義し、すべての方向のグリッドの`extent`（長さ）を定義するか、開始点と終了点（`x`、`y`、`z`）を定義することによって作成できます。`CharDim`（`GeoParams.jl`で作成された特性寸法を持つ構造体）を指定すると、構造体を作成する前にグリッドを無次元化します。

間隔は、特定の方向で一定であると仮定されます。

これは、中央点のための1Dベクトルも作成するため、ずれたグリッドにも使用できます。`size`で指定した点はコーナーポイントです。

注意: これは主に固体地球科学のアプリケーション向けであるため、2次元目はz（垂直）と呼ばれます。

# 例

====

無次元単位の基本的なケース:

```julia
julia> Grid = create_CartGrid(size=(10,20),x=(0.,10), z=(2.,10))
Grid{Float64, 2}
           size: (10, 20)
         length: (10.0, 8.0)
         domain: x ∈ [0.0, 10.0], z ∈ [2.0, 10.0]
 grid spacing Δ: (1.1111111111111112, 0.42105263157894735)
```

次元単位の例:

```julia
julia> CharDim = GEO_units()
julia> Grid    = create_CartGrid(size=(10,20),x=(0.0km, 10km), z=(-20km, 10km), CharDim=CharDim)
CartGrid{Float64, 2}
           size: (10, 20)
         length: (0.01, 0.03)
         domain: x ∈ [0.0, 0.01], z ∈ [-0.02, 0.01]
 grid spacing Δ: (0.0011111111111111111, 0.0015789473684210528)

```
