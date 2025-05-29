```
GoalConstraint{P,T}
```

形の制約 $x_g = a$、ここで $x_g$ は状態ベクトルの一部のみです。

# コンストラクタ:

```julia
GoalConstraint(xf::AbstractVector)
GoalConstraint(xf::AbstractVector, inds)
```

ここで `xf` は n 次元の目標状態です。`inds` が提供されている場合、`xf[inds]` のみが使用されます。
