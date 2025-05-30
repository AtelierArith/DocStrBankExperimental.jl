```julia
struct PersonParameterResult{T<:AbstractItemResponseModels.ItemResponseModel, U<:PersonParameters.PersonParameter, V<:PersonParameters.PersonParameterAlgorithm} <: AbstractArray{U<:PersonParameters.PersonParameter, 1}
```

推定された個人パラメータのコレクション。

## フィールド

  * `values`: 推定された個人パラメータのベクトル
  * `algorithm`: 推定に使用されたアルゴリズム

## メソッド

  * [`modeltype`](@ref): スケーリングモデルのモデルタイプを取得
  * [`algorithm`](@ref): 推定に使用されたアルゴリズムを取得
