```
delaunay(dim::Integer, numpoints::Integer, points::AbstractVector,
    [flags::AbstractString]) → Matrix{Int32}
```

任意の次元 `dim` の点のクラウドのデローニ三角形分割を計算します。ベクトル `points` は「コンポーネント主要順序」でデータを保持しており、すなわち、コンポーネントはベクトル内で連続しています。したがって、ベクトル `points` の長さは `dim * numpoints` でなければなりません。

返される行列は形状 `(dim + 1, nsimplices)` を持ち、ここで `nsimplices` は計算されたデローニ三角形分割の単体の数です。

Qhull が使用するデフォルトのフラグセットをオーバーライドするには、追加の位置引数 `flags` を渡します。デフォルトのフラグセットは、3次元までの場合は `qhull d Qt Qbb Qc Qz` であり、高次元の場合は `qhull d Qt Qbb Qc Qx` です。渡すフラグはデフォルトのフラグをオーバーライドします。つまり、Qhull が使用すべきすべてのフラグを渡す必要があります。

## 例: 列主要順序の点のベクトルを渡す

この場合、次元と点の数を指定する必要があります。

```julia
using MiniQhull
dim          = 2
numpoints    = 4
coordinates  = [0,0,0,1,1,0,1,1]
connectivity = delaunay(dim, numpoints, coordinates)
# 出力
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

```
delaunay(points::AbstractMatrix, [flags::AbstractString]) -> Matrix{Int32}
```

このバリアントでは、点のクラウドは `size(matrix) == (dim, numpoints)` の行列によって指定されます。

## 例: 点の行列を渡す

```julia
using MiniQhull
coordinates  = [0 0 1 1; 0 1 0 1]
connectivity = delaunay(coordinates)
# 出力
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

```
delaunay(points::AbstractVector{T}, [flags::AbstractString]) where T -> Matrix{Int32}
```

このバリアントでは、点のクラウドは点のベクトルによって指定されます。

`points` は `Vector{Vector}` であることができますが、これは遅くなります。なぜなら、データをフラット化して収集する必要があるため、Qhull にデータを渡す前に処理が必要です。

```julia
pts = [[0.,0.], [0.,1.], [1.,0.], [1.,1.]]
delaunay(pts)
# 出力
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

より効率的な代替手段は、`points` が列主要ベクトルと同じメモリレイアウトを持つ場合です。つまり、`T` が `reinterpret(Float64, points)` が点の列主要ベクトルを生成するような型である場合です。これにより、余分なメモリ割り当てを回避でき、大量の点を三角形分割する必要がある場合に便利です。例としては、等長のタプルや `SVector` を使用して点を表現することが挙げられます。

```julia
using MiniQhull, StaticArrays
dim = 3
npts = 500
pts = [SVector{dim, Float64}(rand(dim)) for i = 1:npts];
flags = "qhull d Qbb Qc QJ Pp" # 一部のカスタムフラグ
connectivity = delaunay(pts, flags)
```
