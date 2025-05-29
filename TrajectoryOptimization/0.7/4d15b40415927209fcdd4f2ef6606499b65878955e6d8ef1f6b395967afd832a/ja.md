```
CollisionConstraint
```

状態に対してペアワイズの自己衝突しない制約を強制します。これは、`norm(x[x1] - x[x2]).^2 ≥ r^2` となるように、`x1` と `x2` がそれぞれの物体の位置のインデックスであり、`r` が衝突半径であることを意味します。

# コンストラクタ

CollisionConstraint(n::Int, x1::AbstractVector{Int}, x2::AbstractVector{Int}, r::Real)
