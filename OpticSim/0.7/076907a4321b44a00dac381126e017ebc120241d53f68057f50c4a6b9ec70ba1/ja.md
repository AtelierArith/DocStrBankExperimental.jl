```
HologramInterface{T} <: OpticalInterface{T}
```

*厚い*ホログラムを表すインターフェース（幾何学的には薄い）。効率 `η` はKogelnikの結合波理論を使用して計算されるため、一次のみに有効です。ゼロ次が含まれる場合、効率は `1 - η` になります。また、HOEが再生条件と類似の条件下で記録されたと仮定し、`thickness` はマイクロメートル単位です。

`BeatState` の引数は `ConvergingBeam`、`DivergingBeam`、および `CollimatedBeam` のいずれかです。最初の2つの場合、`signalpointordir` と `referencepointordir` はグローバル座標空間の3Dポイントです。`CollimatedBeam` の場合、それらは正規化された方向ベクトルです。

参考文献：

  * *Coupled Wave Theory for Thick Hologram Gratings* - H Kogelnik, 1995
  * *Sequential and non-sequential simulation of volume holographic gratings* - M Kick et al, 2018

```julia
HologramInterface(signalpointordir::SVector{3,T}, signalbeamstate::BeamState, referencepointordir::SVector{3,T}, referencebeamstate::BeamState, recordingλ::T, thickness::T, beforematerial, substratematerial, aftermaterial, signalrecordingmaterial, referencerecordingmaterial, RImodulation::T, include0order  = false)
```
