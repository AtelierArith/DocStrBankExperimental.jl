```
vtmanhattan(x::AbstractArray, y::AbstractArray; dims=:)
```

ベクトルが次元 `dims` に沿ったスライスに対応する間のマンハッタン距離を計算します。スレッド化されています。

参照: [`vteuclidean`](@ref), [`vtchebyshev`](@ref), [`vtminkowski`](@ref)
