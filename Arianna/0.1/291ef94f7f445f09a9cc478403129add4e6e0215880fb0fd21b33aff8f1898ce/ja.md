```
StoreParameters{V<:AbstractArray} <: AriannaAlgorithm
```

パラメータストアを表す構造体。

# フィールド

  * `paths::Vector{String}`: パラメータファイルへのパスのベクター
  * `files::Vector{IOStream}`: パラメータファイルへのオープンファイルストリームのベクター
  * `parameters_list::V`: 保存するパラメータのリスト
  * `store_first::Bool`: 最初のステップでパラメータを保存するフラグ
  * `store_last::Bool`: 最後のステップでパラメータを保存するフラグ

# 型パラメータ

  * `V`: パラメータ配列の型
