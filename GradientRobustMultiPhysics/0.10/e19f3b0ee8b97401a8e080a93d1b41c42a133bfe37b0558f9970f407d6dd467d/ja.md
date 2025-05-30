```julia
LagrangeMultiplier(
    operator::Type{<:??};
    name,
    AT,
    action,
    regions,
    store,
    factor
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

ビリニア形式を記述するためのコンストラクタ a(u,v) = (A(operator(u)), id(v)) であり、転置されたPDE座標のブロックに転置された第二のブロックを組み立てます。このオペレーターをPDE記述の対応する下対角ブロックに置くことによって、PDEの一つの未知数を他の未知数のラグランジュ乗数としてレンダリングするために使用されることを意図しています。

例: LagrangeMultiplier(Divergence) は、ストークスプロトタイプにおける速度の発散制約のラグランジュ乗数として圧力をレンダリングするために使用されます。
