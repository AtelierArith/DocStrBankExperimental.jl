```
check_params(index::String, params::Dict, indices::Dict)
```

スペクトルインデックス計算に必要なすべてのバンドがパラメータ辞書に含まれているかを確認します。

# 引数

  * `index::String`: 確認するスペクトルインデックスの名前。
  * `params::Dict`: 必要なバンドを確認するためのパラメータ辞書。
  * `indices::Dict`: スペクトルインデックスに関する情報を含む辞書。

# 戻り値

  * `None`

# 例

```julia
# NDVIインデックスのパラメータを確認
index_name = "NDVI"
parameters = Dict("N" => 0.6, "R" => 0.3, "G" => 0.7)
indices = _get_indices()

# パラメータが必要なバンドを含んでいるか確認
check_params(index_name, parameters, indices)
```
