```
str_add!(tr::Tract{T}, xyz::Vector{Matrix{Txyz}}, scalars::Union{Vector{Matrix{Ts}}, Vector{Vector{Ts}}, Nothing}=nothing, properties::Union{Matrix{Tp}, Vector{Tp}, Nothing}=nothing) where {T<:Number, Txyz<:Number, Ts<:Number, Tp<:Number}
```

新しいストリームラインをデータ型 T の Tract 構造に追加します

# 必要な入力

  * tr::Tract{T}: ストリームラインが追加される Tract 構造
  * xyz::Vector{Matrix}: 新しいストリームライン上の点のボクセル座標 [nstr][3 x npts]

# オプションの入力（Tract 構造に含まれている場合のみ必要）

  * scalars::Union{Vector{Matrix}, Vector{Vector}, Nothing}: 新しいストリームライン上の各点に関連付けられたスカラー [nstr][nscalar x npts] または (nscalar == 1 の場合) [nstr][npts]
  * properties::Union{Matrix, Vector, Nothing}: 新しいストリームラインの各点に関連付けられたプロパティ [nprop x nstr] または (nprop == 1 の場合) [nstr]
