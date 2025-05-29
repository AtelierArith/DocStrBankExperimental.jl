```
fitcontinuum(
  spec::Spectrum,
  det::EDSDetector,
  resp::AbstractArray{<:Real,2}; #
  minE::Float64 = 1.5e3,
  maxE::Float64 = 0.95 * spec[:BeamEnergy],
  brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,
  mc::Type{<:MatrixCorrection} = Riveros1993,
)
```

スペクトル内のデータから決定されたROI（:Composition, :BeamEnergy & :TakeOffAngle）から連続体をフィットします。ROIは`continuumrois(...)`を使用して計算され、各ROIは別々にフィットされます。
