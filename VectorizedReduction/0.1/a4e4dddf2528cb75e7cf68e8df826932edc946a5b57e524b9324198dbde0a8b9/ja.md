```
vminkowski(x::AbstractArray, y::AbstractArray, p::Real; dims=:)
```

ベクトルが次元 `dims` に沿ったスライスに対応するミンコフスキー距離を計算します。

`p` は任意の数値を取ることができます（すべての値が数学的に有効なベクトルノルムを生成するわけではありません）。`vminkowski(x, y, Inf)` は `abs.(x .- y)` の中で最大の値を返し、`vminkowski(x, y, -Inf)` は最小の値を返します。

関連情報: [`vmanhattan`](@ref), [`veuclidean`](@ref), [`vchebyshev`](@ref)
