```julia
fittedcontinuum(     spec::Spectrum,     det::EDSDetector,     resp::AbstractArray{<:Real,2}; #     mode = :Global [ | :Local ] # Fit to all ROIs simultaneously (:Global) or to each roi independently (:Local)     minE::Float64 = 1.5e3,     maxE::Float64 = 0.95 * spec[:BeamEnergy],     width::Int = 20, # Width of ROI at each end of each patch of continuum that is matched     brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,     mc::Type{<:MatrixCorrection} = Riveros1993,   )::Spectrum

特性ピークの下の連続体を、最も近い連続体ROIをフィッティングすることによってフィットします。低エネルギーのピークは、エネルギーがすぐに高い連続体を使用してフィットされ、高エネルギーのピークは、両側の連続体を使用してフィットされます。

  * mode = :Global [ | :Local ] グローバルは、単一のスケールファクターを使用してデータにモデルをフィットします。:Localは、特性ピークの上と下のROIでグローバルモデルを微調整します。

通常、:Globalは全体的に最良のフィットを生成しますが、:Localは特性ピークの周りでより良いフィットを提供し、ピークの下の連続体をモデル化するのに適しています。
```
