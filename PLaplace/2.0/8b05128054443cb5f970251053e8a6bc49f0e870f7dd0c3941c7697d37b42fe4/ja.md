```julia
xpnorm(
    p::Float64,
    v::AbstractVector{Float64},
    D::AbstractDict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}},
    w::AbstractVector{Float64}
) -> Float64

```

前の `xpnorm(...)` と同じですが、導関数ベクトルの代わりに係数ベクトルと導関数テンソルを引数として取ります。

新しい必須引数が必要です

  * `v::AbstractVector{Float64}`: メッシュのノードで離散的に評価された関数。
  * `D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}}`: v と同じノードに対応する離散導関数テンソル。

これは

  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}`

に置き換わります。
