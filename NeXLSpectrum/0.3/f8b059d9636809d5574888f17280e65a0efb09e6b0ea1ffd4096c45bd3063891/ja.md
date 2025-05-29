```
suitablefor(
    elm::Element, 
    matOrElms::Union{Material, AbstractSet{Element}}, 
    det::Detector; 
    maxE::Float64 = 1.0e6, 
    ampl::Float64 = 1.0e-5,
    warnme::Bool = true
)::Vector{Tuple{Vector{CharXRay}, UnitRange{Int64}}}
```

材料または `Element` のコレクションが、要素 `elm` に対して、検出器 `det` の適切な参照となるROIはどれですか？この関数は、材料の適合性に応じて情報、警告、およびエラーメッセージを提供します。
