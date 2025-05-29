```julia
struct TemperingParameter{T<:AbstractFloat}
```

テンプラリングパラメータの更新に関する情報を保持します。基本的なロジスティック関数のパラメータです。

# フィールド

  * `L::AbstractFloat`
  * `k::AbstractFloat`
  * `x₀::AbstractFloat`
