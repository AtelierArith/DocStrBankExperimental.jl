```
dosenormalize(spectrum::Spectrum{T}, dose=60.0)::Spectrum{T} where { T <: Real }
dosenormalize(spectrum::Spectrum{T}, dose=60.0)::Spectrum{Float64} where { T <: Integer }
```

`spectrum`を`dose`に等しいライブタイムとプローブ電流にスケールされたスペクトルを計算します。これは、同等の取得時間スケールでスペクトルを設定するのに便利です。
