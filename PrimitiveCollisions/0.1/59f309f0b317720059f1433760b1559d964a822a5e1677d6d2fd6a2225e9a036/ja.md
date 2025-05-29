```julia
function closest_pair(a::AbstractShape{2}, b::AbstractShape{2}, state::State{R})
```

2つの形状 `a` と `b` および `a` に対する `b` の位置と回転を記述する `state` が与えられたとき、互いに最も近い `a` と `b` の境界上の点を返します。交差しない形状にのみ有効です。
