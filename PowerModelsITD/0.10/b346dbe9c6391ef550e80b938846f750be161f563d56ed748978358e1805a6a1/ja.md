```
function apply_voltage_angle_difference_bounds!(
    pmitd_data::Dict{String,<:Any},
    vad::Real=5.0
)
```

`vad::Real` で与えられた電圧角度差の制約の対応する変換を適用します（*すなわち*、ある線の一端から別の端への角度の許容ドリフト）をすべての線に対して、`pmd` 辞書に適用します。
