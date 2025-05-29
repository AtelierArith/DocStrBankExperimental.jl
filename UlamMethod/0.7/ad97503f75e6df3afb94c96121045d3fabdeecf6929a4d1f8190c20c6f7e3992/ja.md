```
struct Boundary{Dim, M, CRS}
```

ウラムの方法が適用される計算領域のコンテナ型です。

境界は、座標参照系 `CRS` を持つ多様体 `M` に埋め込まれた次元 `Dim` を持っています。

境界は [`BinningAlgorithm`](@ref) に従って分割されます。

### フィールド

  * `boundary`: 境界を定義する `Polytope`。

### メソッド

```
points(boundary)
```

境界の頂点の `Dim x N` 行列を計算します。

### 1D コンストラクタ

```
Boundary(x_start, x_end)
```

境界は `x_start` と `x_end` の間の連続した線分 `Segment` です。

### 2D コンストラクタ

```
Boundary(verts)
```

境界は頂点 `verts` を持つ閉じた多角形 `Ngon` であり、`verts` は `(x, y)` 座標のベクトルまたは `2 x N` 行列である必要があります。

```
Boundary(xmin, xmax, ymin, ymax)
```

長方形の境界の場合の便利なコンストラクタも提供されています。

### ≥3D コンストラクタ

```
Boundary(corner_min, corner_max)
```

境界は最小および最大の頂点 `corner_min`, `corner_max` を持つ `HyperRectangle` であり、コーナーは `NTuple` で、`(x_min, y_min, z_min, ...)`, `(x_max, y_max, z_max, ...)` です。

### 自動境界構築

```
AutoBoundary(traj; nirvana = 0.10)
```

`traj` の [`Trajectories`](@ref) に基づいて任意の次元で長方形の境界を構築します。

境界は、データの一部 `nirvana` がニルヴァーナにあるように配置されます。たとえば、デフォルト値 `0.10` の場合、すべてのデータポイントの約 `10%`（`x0` と `xT` の間で分割される）が境界の外にあり、両側にほぼ同じ量があります。

境界の形状は、`min`（それぞれ `max`）が各次元に沿って境界の「下」に（それぞれ「上」に）なるように、タプルの形 `(min, max)` の長さ `Dim` のベクトルとして `nirvana` を提供することでさらに制御できます。

```
AutoBoundary2D(traj; nirvana = 0.10, tol = 0.001)
```

`traj` の [`Trajectories`](@ref) に基づいて、2次元でタイトな境界を構築します。

問題の境界は、データの凸包をスケーリングして形成され、データの一部 `nirvana` が境界の外に `tol` パーセント以内にあるようにします。
