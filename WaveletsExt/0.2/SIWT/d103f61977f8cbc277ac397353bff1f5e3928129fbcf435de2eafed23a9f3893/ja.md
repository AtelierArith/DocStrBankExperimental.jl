```
ShiftInvariantWaveletTransformObject(signal, wavelet)
```

SIWTオブジェクトの外部コンストラクタと初期化。

# 引数

  * `signal::Array{T} where T<:AbstractFloat`: 入力信号。
  * `wavelet::OrthoFilter`: ウェーブレットフィルタ。
  * `maxTransformLevel::S where S<:Integer`: (デフォルト: `0`) 最大変換レベル。
  * `maxShiftedTransformLevel::S where S<:Integer`: (デフォルト: `0`) 最大シフト変換レベル。
