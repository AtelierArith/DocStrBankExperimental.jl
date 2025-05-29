```
ConvexHull{N, S1<:LazySet{N}, S2<:LazySet{N}} <: ConvexSet{N}
```

2つの集合の和集合の凸包を表す型、すなわち集合

$$
Z = \{z ∈ ℝ^n : z = λx + (1-λ)y,\qquad x ∈ X, y ∈ Y,λ ∈ [0, 1] \}.
$$

### フィールド

  * `X` – 集合
  * `Y` – 集合

### 注意事項

`EmptySet`は`ConvexHull`の中立要素です。

この型は常に凸です。

### 例

2つの100次元ユークリッド球の凸包：

```jldoctest
julia> b1, b2 = Ball2(zeros(100), 0.1), Ball2(4*ones(100), 0.2);

julia> c = ConvexHull(b1, b2);

julia> typeof(c)
ConvexHull{Float64, Ball2{Float64, Vector{Float64}}, Ball2{Float64, Vector{Float64}}}
```
