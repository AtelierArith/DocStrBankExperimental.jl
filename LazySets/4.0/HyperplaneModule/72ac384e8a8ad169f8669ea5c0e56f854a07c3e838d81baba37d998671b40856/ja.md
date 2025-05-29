```
Hyperplane{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

形式 $a⋅x = b$ のハイパープレーンを表す型です。

### フィールド

  * `a` – 法線方向（ゼロでない）
  * `b` – 制約

### 例

平面 $y = 0$:

```jldoctest
julia> Hyperplane([0, 1.], 0.)
Hyperplane{Float64, Vector{Float64}}([0.0, 1.0], 0.0)
```
