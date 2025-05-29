```
compute_derivative(
    D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}},
    v::AbstractVector{Float64}
) -> Dict{Tuple{Int64, Int64}, AbstractVector{Float64}}
```

関数の係数ベクトル v を使用して、離散導関数テンソル D によるすべての一次偏導関数 $D^{(j,r)}v$ の係数ベクトルを返します。各キーのタプル (j,r) は、成分 r の x_j 方向の導関数を表します。
