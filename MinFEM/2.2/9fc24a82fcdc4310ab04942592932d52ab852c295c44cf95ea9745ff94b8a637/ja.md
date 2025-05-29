```julia
parentcoordinates(
    x::Vector{Float64},
    id::Int64
) -> Vector{Float64}

```

d-1 次元の参照要素で与えられた座標を、ローカル境界 id で指定された d 次元の参照要素の境界上の座標にマッピングします。これは、境界の数値積分点をそれぞれの親座標にマッピングするために使用できます。
