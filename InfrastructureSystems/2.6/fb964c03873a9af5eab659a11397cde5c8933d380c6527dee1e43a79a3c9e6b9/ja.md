```julia
get_slopes(
    pwl::InfrastructureSystems.PiecewiseLinearData
) -> Vector{Float64}

```

PiecewiseLinearDataで定義された線分の傾きを計算し、基になる点の数よりも1つ少ない傾きを返します。
