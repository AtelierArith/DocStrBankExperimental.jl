```
fitcontinuum(
  spec::Spectrum,
  resp::AbstractArray,
  rois::Vector{UnitRange};
  brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,
  mc::Type{<:MatricCorrection} = Riveros1993,
)

指定されたチャンネルの範囲（`rois`）に連続体モデルをフィットさせます。`resp`引数は、チャンネルごとの検出器応答を記述する行列です。これは、`EDSDetector`と`DetectorEfficiency`を使用して`resp = NeXLSpectrum.detectorresponse(det, eff)`で計算できます。`Spectrum`オブジェクトは、:Composition、:BeamEnergy、および:TakeOffAngleプロパティが定義されている必要があります。
```
