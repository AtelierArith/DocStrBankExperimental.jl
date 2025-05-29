```julia
struct PersonParameterResult{T<:AbstractItemResponseModels.ItemResponseModel, U<:PersonParameters.PersonParameter, V<:PersonParameters.PersonParameterAlgorithm} <: AbstractArray{U<:PersonParameters.PersonParameter, 1}
```

推定された人のパラメータのコレクション。

## フィールド

  * `values`: 推定された人のパラメータのベクトル
  * `algorithm`: 推定に使用されたアルゴリズム

## メソッド

  * [`modeltype`](@ref): スケーリングモデルのモデルタイプを取得する
  * [`algorithm`](@ref): 推定に使用されたアルゴリズムを取得する
