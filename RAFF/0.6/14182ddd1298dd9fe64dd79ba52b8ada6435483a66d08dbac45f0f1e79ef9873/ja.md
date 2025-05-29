```
generate_clustered_noisy_data(model::Function, n::Int, np::Int,
    p::Int, x_interval::Tuple{Float64,Float64},
    cluster_interval::Tuple{Float64, Float64}; kwargs...)

generate_clustered_noisy_data(model::Function, n::Int,
    np::Int, p::Int, θSol::Vector{Float64},
    x_interval::Tuple{Float64,Float64},
    cluster_interval::Tuple{Float64, Float64}; kwargs...)
```

クラスタリングされた外れ値を持つテストセットを生成します。

引数とオプションの引数は、タプル `cluster_interval` を除いて [`generate_noisy_data!`](@ref) と同じであり、`cluster_interval` はクラスタリングされた外れ値を生成するための区間です。

戻り値はタプル `(data, θSol, outliers)` であり、次のようになります。

  * `data`: (`np` x `3`) 配列で、各行には `x` と `model(x, θSol)` が含まれています。引数として与えられたのと同じ配列です。
  * `θSol`: 正確な解を持つ `n` 次元ベクトル。
  * `outliers`: このデータセットの外れ値。引数として与えられたのと同じベクトルです。
