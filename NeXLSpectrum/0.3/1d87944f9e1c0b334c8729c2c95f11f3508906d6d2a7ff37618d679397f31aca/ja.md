```
charXRayLabels(#
  spec::Spectrum, #
  elm::Element, #
  allElms::AbstractSet{Element}, #
  det::Detector, #
  ampl::Float64, #
  maxE::Float64=1.0e6)::Vector{SpectrumFeature}
```

'spec'に含まれる元素'allElms'に関連するCharXRayLabelオブジェクトのベクターを作成します。これは'det'で収集されたと仮定します。'allElms'の他の元素が'elm'と干渉するROIは含まれません。
