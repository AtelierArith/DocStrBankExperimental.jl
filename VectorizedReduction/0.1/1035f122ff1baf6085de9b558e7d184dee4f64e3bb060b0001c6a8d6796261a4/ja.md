```
vtchebyshev(x::AbstractArray, y::AbstractArray; dims=:)
```

ベクトルが次元 `dims` に沿ったスライスに対応する間のチェビシェフ距離を計算します。スレッド対応。

参照: [`vtmanhattan`](@ref), [`vteuclidean`](@ref), [`vtminkowski`](@ref)
