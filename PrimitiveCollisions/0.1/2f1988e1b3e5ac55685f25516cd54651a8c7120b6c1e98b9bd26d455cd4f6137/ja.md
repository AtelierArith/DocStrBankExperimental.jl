```julia
function check_collision(a::AbstractShape{2}, b::AbstractShape{2}, state::State{R}) where {R}
```

2つの形状 `a` と `b` および `a` に対する `b` の位置と回転を記述する `state` を与えると、彼らの分離を記述する [`CollisionData`](@ref) を返します。
