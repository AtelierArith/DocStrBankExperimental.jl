```
extents(cxrs::AbstractVector{<:SpectrumFeature},det::Detector,ampl::Float64)::Vector{UnitRange{Int}}
```

指定された検出器で測定されるX線の指定されたコレクションの連続したチャネル範囲を決定します。 amplは各ピークの範囲を決定します。
