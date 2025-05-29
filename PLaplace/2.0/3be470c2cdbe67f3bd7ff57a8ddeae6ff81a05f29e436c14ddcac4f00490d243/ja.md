```
xpnorm(
    p::Float64,
    f::Function,
    mesh::Mesh;
    qdim::Int64 = 1
) -> Float64
```

前の `xpnorm(...)` と同じですが、離散導関数（テンソル）と係数ベクトルの代わりに連続関数とメッシュを引数として取ります。

新しい必須引数が必要です

  * `f::Function`: 評価される関数の解析的記述。
  * `mesh::Mesh`: $T_{h_\Omega}$ に対応する FEM メッシュ。

これにより

  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}` が置き換えられます。
