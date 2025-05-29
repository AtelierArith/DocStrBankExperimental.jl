```
HalfSpace{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

形式 $a⋅x ≤ b$ の（閉じた）半空間を表す型です。

### フィールド

  * `a` – 法線方向（ゼロでない）
  * `b` – 制約

### 例

半空間 $x + 2y - z ≤ 3$:

```jldoctest
julia> HalfSpace([1, 2, -1.], 3.)
HalfSpace{Float64, Vector{Float64}}([1.0, 2.0, -1.0], 3.0)
```

平面で $y ≥ 0$ の集合を表すために、式を $0x - y ≤ 0$ のように再配置できます:

```jldoctest
julia> HalfSpace([0, -1.], 0.)
HalfSpace{Float64, Vector{Float64}}([0.0, -1.0], 0.0)
```
