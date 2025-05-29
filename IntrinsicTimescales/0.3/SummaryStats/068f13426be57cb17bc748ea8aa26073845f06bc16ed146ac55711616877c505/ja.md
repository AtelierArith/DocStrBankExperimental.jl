```
comp_psd(x::AbstractArray{T}, fs::Real; kwargs...) where {T <: Real}
```

パワースペクトル密度を周期グラムまたはウェルチ法を使用して計算します。

# 引数

  * `x`: 時系列データ (時間 × チャンネル)
  * `fs`: サンプリング周波数
  * `dims=ndims(x)`: PSDを計算する次元
  * `method="periodogram"`: 使用する方法 ("periodogram" または "welch")
  * `window=dsp.hamming`: 窓関数
  * `n=div(size(x,dims),8)`: ウェルチ法の窓サイズ
  * `noverlap=div(n,2)`: ウェルチ法のオーバーラップ

# 返り値

  * `power`: パワースペクトル密度の値
  * `freqs`: 対応する周波数

# 注意事項

  * ウェルチ法では、窓サイズとオーバーラップを慎重に考慮してください
  * 基本的な計算にはDSP.jlを使用します
