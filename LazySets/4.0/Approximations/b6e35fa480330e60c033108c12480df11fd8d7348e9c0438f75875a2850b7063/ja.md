```
OctDirections{N, VN} <: AbstractDirections{N, VN}
```

八角形の方向の表現。

### フィールド

  * `n` – 次元

### ノート

八角形の方向は、ほぼすべての場所でゼロであり、2つの次元 $i$, $j$（可能性として $i = j$）で $±1$ であるすべてのベクトルで構成されています。次元 $n$ では、そのような方向が $2n^2$ 存在します。

### 例

テンプレートは次元を渡すことで構築できます。たとえば、次元が2の場合：

```jldoctest dirs_Oct
julia> dirs = OctDirections(2)
OctDirections{Float64, SparseArrays.SparseVector{Float64, Int64}}(2)

julia> length(dirs) # 方向の数
8
```

デフォルトでは、方向はスパースベクトルとして表現されます：

```jldoctest dirs_Oct
julia> eltype(dirs)
SparseArrays.SparseVector{Float64, Int64}
```

2次元では、方向は八角形の面に対して法線です。

```jldoctest dirs_Oct
julia> first(dirs)
2-element SparseArrays.SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [2]  =  1.0

julia> Vector.(collect(dirs))
8-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [1.0, -1.0]
 [-1.0, 1.0]
 [-1.0, -1.0]
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

数値型も指定できます：

```jldoctest
julia> dirs = OctDirections{Rational{Int}}(10)
OctDirections{Rational{Int64}, SparseArrays.SparseVector{Rational{Int64}, Int64}}(10)

julia> length(dirs)
200
```
