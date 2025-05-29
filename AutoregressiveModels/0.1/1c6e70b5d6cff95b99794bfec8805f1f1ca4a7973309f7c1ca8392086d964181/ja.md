```
fit(::Type{<:VARProcess}, data, names, nlag::Integer; kwargs...)
```

`names`でインデックス付けされた変数の`nlag`ラグを使用して、`Tables.jl`互換の`data`テーブルから通常最小二乗法でベクトル自己回帰を推定します。

# キーワード

  * `subset::Union{BitVector, Nothing}=nothing`: 推定に使用する`data`のサブセット。
  * `choleskyresid::Bool=false`: 残差分散共分散行列のためのコレスキー分解を実施します。
  * `adjust_dofr::Bool=true`: 残差分散共分散行列を計算する際に自由度を調整します。
  * `nocons::Bool=false`: 推定に切片項を含めません。
  * `TF::Type=Float64`: 推定に使用される数値型。
