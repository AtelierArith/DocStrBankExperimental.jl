```
generate_clustered_noisy_data!(data::Array{Float64, 2},
    v::Vector{Int}, model::Function, n::Int, np::Int, p::Int,
    x_interval::Tuple{Float64,Float64},
    cluster_interval::Tuple{Float64, Float64}; kwargs...)
```

クラスタリングされた外れ値を持つテストセットを生成します。このバージョンは、(`np` x `3`) 行列 `data` の内容と、`data` 内の外れ値の位置に対する整数インデックスを持つベクター `v` を上書きします。

引数とオプション引数は [`generate_noisy_data!`](@ref) と同じですが、クラスタリングされた外れ値を生成するための区間であるタプル `cluster_interval` を除きます。

戻り値はタプル `(data, θSol, outliers)` であり、次のようになります。

  * `data`: (`np` x `3`) 配列で、各行には `x` と `model(x, θSol)` が含まれています。引数として与えられたのと同じ配列です。
  * `θSol`: 正確な解を持つ `n` 次元ベクター。
  * `outliers`: このデータセットの外れ値。引数として与えられたのと同じベクターです。
