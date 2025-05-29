```
setinvalid_nongrowingseason!(df, tGPP; kwargs...)
```

非成長期を`:valid`列でfalseに設定します。

# 引数

  * `df`: `:GPP`と`:datetime`の列を持つDataFrame
  * `tGPP`: 日次GPPのスカラー閾値（[`get_growingseason`](@ref)を参照）

オプション:

  * `update_GPPd`: trueに設定すると、[`get_growingseason`](@ref)からの結果に基づいて`:GPPd_smoothed`列も追加で更新します
  * その他は[`get_growingseason`](@ref)に渡されます

# 値

`:valid`列と`:GPPd_smoothed`が修正されたdfで、すべての非成長期のレコードがfalseに設定されます。
