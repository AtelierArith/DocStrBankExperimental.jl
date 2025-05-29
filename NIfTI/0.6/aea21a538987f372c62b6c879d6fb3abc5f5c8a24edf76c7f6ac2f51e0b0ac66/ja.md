```
NIVolume{T<:Number,N,R} <: AbstractArray{T,N}
```

`N`次元のNIfTIボリュームで、型`R`の生データを持ちます。`R <: Number`の場合、`Float32`に変換されます。さらに、ヘッダーは生ボリュームと一貫性を持つように自動的に更新されます。

# メンバー

  * `header`: `NIfTIHeader`
  * `extensions`: `NIfTIExtension`のベクター
  * `raw`: 型`R`の生データ
