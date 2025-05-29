```
halfspace_left(p::AbstractVector, q::AbstractVector)
```

2次元の2点を通る線分の「左」を表す半空間を返します。

### 入力

  * `p` – 最初の点
  * `q` – 2番目の点

### 出力

2点 `p` と `q` を通る境界を持ち、指向された線分 `pq` の左側を表す半空間。

### アルゴリズム

半空間 $a⋅x ≤ b$ は `a = [dy, -dx]` として計算されます。ここで、$d = (dx, dy)$ は線分 `pq` を示し、すなわち $\vec{d} = \vec{p} - \vec{q}$ であり、`b = dot(p, a)` です。

### 例

2次元における「東」と「西」の方向の左半空間は、上半空間と下半空間です：

```jldoctest halfspace_left
julia> using LazySets: halfspace_left

julia> halfspace_left([0.0, 0.0], [1.0, 0.0])
HalfSpace{Float64, Vector{Float64}}([0.0, -1.0], 0.0)

julia> halfspace_left([0.0, 0.0], [-1.0, 0.0])
HalfSpace{Float64, Vector{Float64}}([0.0, 1.0], 0.0)
```

その辺を表す線分の列からボックスを作成します：

```jldoctest halfspace_left
julia> H1 = halfspace_left([-1.0, -1.0], [1.0, -1.0]);

julia> H2 = halfspace_left([1.0, -1.0], [1.0, 1.0]);

julia> H3 = halfspace_left([1.0, 1.0], [-1.0, 1.0]);

julia> H4 = halfspace_left([-1.0, 1.0], [-1.0, -1.0]);

julia> H = HPolygon([H1, H2, H3, H4]);

julia> B = BallInf([0.0, 0.0], 1.0);

julia> B ⊆ H && H ⊆ B
true
```
