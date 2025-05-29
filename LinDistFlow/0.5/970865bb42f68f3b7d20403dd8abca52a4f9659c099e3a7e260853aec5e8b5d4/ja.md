```
constrain_line_amps(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

推定されたラインアンペアを、正方向と負方向の両方で `p.Isquared_up_bounds` を使用して制約します。

詳細については `define_line_amps_pu` を参照してください。
