```
vtminkowski(x::AbstractArray, y::AbstractArray, p::Real; dims=:)
```

ベクトルが次元 `dims` に沿ったスライスに対応するミンコフスキー距離を計算します。スレッド化されています。

`p` は任意の数値を取ることができます（すべての値が数学的に有効なベクトルノルムを生成するわけではありません）。`vtminkowski(x, y, Inf)` は `abs.(x .- y)` の中で最大の値を返し、`vtminkowski(x, y, -Inf)` は最小の値を返します。

関連情報: [`vtmanhattan`](@ref), [`vteuclidean`](@ref), [`vtchebyshev`](@ref)
