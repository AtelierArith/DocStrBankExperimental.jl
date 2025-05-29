```
post!(gl, gr, gd, ::StataPostHDF, cr::ContrastResult, left::Int=2, right::Int=3; kwargs...)
```

`cr`から`left`と`right`でインデックスされた係数の最小二乗重みをStataモジュール[`posthdf`](https://github.com/junyuan-chen/posthdf)にエクスポートします。2つの係数の違いに対する各セルの寄与も計算され、エクスポートされます。重みと寄与は、それぞれ3つのグループ`gl`、`gr`、`gd`に係数推定値として保存されます。グループは`HDF5.Group`または文字列でインデックス可能なオブジェクトである必要があります。

# キーワード

  * `lefttag::String=string(left)`: `left`でインデックスされた係数のために`"l_"`で接頭辞が付けられた後、Stataで`depvar`として使用される名前。
  * `righttag::String=string(right)`: `right`でインデックスされた係数のために`"r_"`で接頭辞が付けられた後、Stataで`depvar`として使用される名前。
  * `model::String="InteractionWeightedDIDs.ContrastResult"`: モデルの名前。
  * `eqnames::Union{AbstractVector, Nothing}=nothing`: Stataの係数名に接頭辞を付ける方程式名。
  * `colnames::Union{AbstractVector, Nothing}=nothing`: Stataで係数名として使用される列名。
  * `at::Union{AbstractVector{<:Real}, Nothing}=nothing`: Stataの`at`ベクトル。
