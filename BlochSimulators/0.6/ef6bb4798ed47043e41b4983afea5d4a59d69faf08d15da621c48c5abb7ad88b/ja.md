```
pSSFP3D{T<:AbstractFloat,N,U<:AbstractVector{Complex{T}},V<:Number} <: IsochromatSimulator{T}
```

この構造体は、アイソクロマットモデルに基づいた可変フリップ角スキームを持つ反転回復、勾配バランス、過渡状態シーケンスをシミュレートするために使用されます。TRとTEはシーケンス全体で固定されています。RF励起波形は時間で離散化できますが、スライスプロファイルメカニズムは提供されていません。このシーケンスは、反転後に「α/2」プレパルスも使用します。

# フィールド

  * `RF_train::U` 各TRのフリップ角を持つベクトルで、abs.(RF*train)はRFフリップ角（度単位）であり、angle.(RF*train)はRF位相（度単位）であるべきです。
  * `TR::T`: シーケンス中に一定と仮定される繰り返し時間（秒単位）
  * `γΔtRF::SVector{N}{V}`: フリップ角1度に正規化された時間離散化されたRF波形
  * `Δt::NamedTuple{(:ex, :inv, :pr),NTuple{3,T}}`: 励起パルス（ex）、反転遅延（inv）、RFとTEの間の時間（pr）の各サンプルの時間間隔
