```
vteuclidean(x::AbstractArray, y::AbstractArray; dims=:)
```

スライスに沿った次元 `dims` に対応するベクトル間のユークリッド距離を計算します。スレッド処理されています。

参照: [`vtmanhattan`](@ref), [`vtchebyshev`](@ref), [`vtminkowski`](@ref)
